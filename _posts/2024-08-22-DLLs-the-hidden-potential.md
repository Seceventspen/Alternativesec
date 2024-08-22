---
layout: post
title: 'Understanding DLLs: The Hidden Potential for Cybersecurity Threats'
tags: [Pentest, tool, Tips]
featured_image_thumbnail: assets/images/posts/dll/dll-title-design.png
featured_image: assets/images/posts/dll/dll-title-design.png
featured: true
hidden: true
---

Yesterday I was asked a couple of questions by someone that I mentor/help along the way with their own cyber security journey, to do with a few topics they are starting to look into. One such question asked was:

>"What is a DLL and how can they be used for exploitation"

Now, I know the answer to this, but I found my repsonse to the individual in question, somewhat lacking, which made me feel a little disappointed in myself. So to that end, I thought I'd do a "do over", so what did I do, I wrote a blog post about the answer of course, or rather my "Interpretation"  of it.

Nothing new or ground breaking here, seasoned pentesters/red teamers/malware devs might want to skip it, but hopefully it's better than the "wooly" explanation I provided yesterday... lol

<!--more-->

In the realm of Windows operating systems, Dynamic Link Libraries (DLLs) are essential components that contribute significantly to the functionality and modularity of applications. However, their very nature also makes them a prime target for abuse by threat actors. In this blog post, we'll delve into what DLLs are, how they can be exploited, and the types of functions that can be used to execute malicious code.

# What is a DLL?

A Dynamic Link Library (DLL) is a file containing code and data that can be used by multiple programs simultaneously. Unlike an executable (EXE) file, which is a standalone application, a DLL provides functions that applications can call to perform specific tasks. This modular approach allows for more efficient memory usage, easier updates, and shared functionality across different programs.

For example, `user32.dll` is a well-known DLL in Windows that provides essential functions for handling user input (like keyboard and mouse interactions), window management, and other graphical user interface tasks. Programs can call on `user32.dll` to perform these functions without having to include the code directly within their own executables.

# How DLLs Can Be Abused

While DLLs are incredibly useful for legitimate software development, they also present a significant risk when exploited by malicious actors. Here are some common ways DLLs can be abused:

### DLL Injection

DLL injection is a technique used by attackers to inject malicious code into a running process by loading a rogue DLL. This is often achieved by exploiting legitimate functions within the Windows API, such as `CreateRemoteThread` and `LoadLibrary`. Once the malicious DLL is injected, it runs within the context of the targeted application, making it difficult to detect and potentially allowing the attacker to execute arbitrary code, steal data, or further compromise the system.

**Example Scenario:** An attacker could inject a malicious DLL into a web browser process. This DLL could then hook into the browser's functionality to capture sensitive information such as login credentials or monitor user activity without raising suspicion.

### DLL Hijacking

DLL hijacking, also known as DLL preloading or DLL search order hijacking, takes advantage of the way Windows searches for DLLs. When an application is launched, Windows looks for required DLLs in a specific order. If an attacker places a malicious DLL with the same name as a legitimate one in a directory that is searched before the legitimate DLL's directory, the application may load the malicious DLL instead.

**Example Scenario:** An attacker could place a malicious DLL in the same directory as a vulnerable application. When the application starts, it loads the attacker's DLL, which can then perform any number of malicious actions, from privilege escalation to backdoor installation.

### Reflective DLL Loading

Reflective DLL loading is a technique where a DLL is loaded into memory without using the traditional Windows API calls like LoadLibrary. This technique is often used in memory-only malware to avoid leaving traces on the disk and to evade security software that monitors for file-based activity.

**Example Scenario:** An advanced threat actor could use reflective DLL loading to inject malware into a process without triggering file-based defenses. The malware would reside entirely in memory, making it harder to detect and analyze.

# Functions Required to Execute Malicious Code

To successfully execute malicious code using a DLL, several key functions and techniques are often employed:

### DllMain

`DllMain` is the entry point for a DLL and is automatically called by the operating system when the DLL is loaded, unloaded, or when a new thread is created within the process. A malicious actor can modify `DllMain` to execute arbitrary code when the DLL is loaded, allowing the attacker to gain control as soon as the DLL is injected or hijacked.

### LoadLibrary and GetProcAddress

`LoadLibrary` is a Windows API function that loads a DLL into the memory of the current process. `GetProcAddress` is then used to obtain the address of a function within the loaded DLL. These functions are commonly used in both legitimate applications and in malicious ones to dynamically load and execute code.

### CreateRemoteThread

`CreateRemoteThread` is a function that creates a thread in another process's address space. This is a critical component in DLL injection attacks, as it allows an attacker to force another process to execute code within a different, often privileged, context.

### VirtualAllocEx and WriteProcessMemory

These functions are used to allocate memory and write data to the address space of another process. They are often used in conjunction with `CreateRemoteThread` to inject and execute malicious DLLs in target processes.

# Putting it all together

So now we have an understanding of what a DLL is, types of attacks and some of the known functions required/used to execute malicious code, lets level up a little further by stepping through the actual process loading and executing code.

### Step 1: Identifying the Target Process

- **Objective:** The pentester/red teamer/threat actor must first identify the target process into which they want to inject their malicious code.
- **Description:** The target process is usually one that is highly trusted or has elevated privileges (e.g., a web browser, system service, or a process running under the System account).
- **Tools:** Attackers might use tools like Task Manager, Process Explorer, or even custom scripts to list running processes and identify potential targets based on name, privilege level, or other factors.

### Step 2: Opening a Handle to the Target Process

- **Objective:** Gain access to the target process's memory space.
- **Description:** Using the `OpenProcess` API function, the attacker opens a handle to the target process with the required access rights, such as `PROCESS_ALL_ACCESS`.
- **Execution:** The handle is essentially a pointer that allows the attacker to interact with the process’s memory. Without this handle, the attacker cannot manipulate the target process.

```c
HANDLE hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, targetPID);
```
- **Outcome:** If successful, the attacker now has a handle to the process, allowing them to perform further actions like memory allocation and code injection.

### Step 3: Allocating Memory in the Target Process

- **Objective:** Reserve space in the target process's memory to hold the malicious code (e.g., the DLL payload).
- **Description:** The `VirtualAllocEx` function is used to allocate a block of memory within the target process. The memory is typically allocated with permissions that allow code execution `(PAGE_EXECUTE_READWRITE)`.
- **Execution:** The allocated memory space will hold the malicious DLL or shellcode that the attacker intends to execute.

```c
LPVOID pRemoteMemory = VirtualAllocEx(hProcess, NULL, payloadSize, MEM_COMMIT, PAGE_EXECUTE_READWRITE);
```

- **Outcome:** A region of memory within the target process is allocated, and the attacker can now proceed to copy the malicious code into this space.

### Step 4: Writing the Malicious Code into the Allocated Memory

- **Objective:** Place the malicious code (DLL or shellcode) into the allocated memory space within the target process.
- **Description:** Using the `WriteProcessMemory` function, the attacker writes the malicious code from their own process into the memory space of the target process.
- **Execution:** This step effectively "plants" the malicious code in the target process, setting the stage for its execution.

```c
WriteProcessMemory(hProcess, pRemoteMemory, maliciousCode, payloadSize, NULL);
```

- **Outcome:** The target process now contains the malicious code within its memory, although it has not yet been executed.

### Step 5: Creating a Remote Thread to Execute the Malicious Code

- **Objective:** Trigger the execution of the malicious code within the target process.
- **Description:** The `CreateRemoteThread` function is used to create a new thread in the target process. The starting address of this thread is set to the location of the malicious code that was written into the target process's memory.
- **Execution:** When the thread is created and starts running, it begins executing the malicious code.

```c
HANDLE hThread = CreateRemoteThread(hProcess, NULL, 0, (LPTHREAD_START_ROUTINE)pRemoteMemory, NULL, 0, NULL);
```

- **Outcome:** The malicious code is now actively executing within the context of the target process. Depending on the payload, this could result in a variety of malicious activities, such as spawning a backdoor, escalating privileges, or exfiltrating data.

### Step 6: Cleanup and Stealth

- **Objective:** Conceal the attack and ensure persistence.
- **Description:** After executing the malicious code, the attacker might close the handle to the target process and the created thread to avoid suspicion. Additionally, they may employ techniques to erase traces of the injection or to maintain persistence on the system.
- **Execution:** This might involve calling `CloseHandle` on the process and thread handles, and possibly using more advanced techniques like reflective DLL injection, which doesn’t leave any artifacts on disk.

```C
CloseHandle(hThread);
CloseHandle(hProcess);
```

- **Outcome:** The attack completes with the malicious code running undetected within a legitimate process, making it harder for security tools to detect and mitigate the attack.

# Summary of the Execution Flow

1. **Target Selection:** Identify the process to be compromised.
2. **Access Gaining:** Use `OpenProcess` to obtain a handle to the target process.
3. **Memory Allocation:** Allocate memory in the target process with `VirtualAllocEx`.
4. **Code Insertion:** Write the malicious code into the allocated memory using `WriteProcessMemory`.
5. **Execution:** Create a thread in the target process using `CreateRemoteThread` to execute the malicious code.
6. **Cleanup:** Remove traces and ensure persistence while the malicious code operates.

By understanding these steps, cybersecurity professionals can better anticipate and defend against such attacks. Monitoring for anomalies in these functions (e.g., unusual memory allocation or thread creation) is critical for detecting potential threats early in their lifecycle.

# Defending Against DLL-Based Attacks

Given the potential for abuse, it’s crucial for cybersecurity professionals to implement strategies to defend against DLL-based attacks:

1. **Code Signing:** Ensure all legitimate DLLs are signed with a valid digital certificate. Unsigned DLLs should be treated with suspicion.

2. **Application Whitelisting:** Restrict which DLLs can be loaded by enforcing strict application whitelisting policies.

3. **Monitoring and Logging:** Implement comprehensive logging and monitoring of DLL loads, especially in sensitive or high-value systems. Tools that monitor API calls can provide insight into unusual activity.

4. **Regular Audits:** Regularly audit system directories and application directories to ensure no unauthorized DLLs have been added.

# Conclusion

Dynamic Link Libraries are a double-edged sword in the world of Windows programming. While they are essential for efficient and modular application development, they also present significant risks if misused. By understanding the mechanisms through which DLLs can be exploited, cybersecurity professionals can better defend their systems against these stealthy and potentially devastating attacks.

As always ... Thanks for reading!