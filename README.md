# Hi, I'm **Abderrahmane Sebban** 

> *Cybersecurity Enthusiast · CTF Player · Low-level Developer*

---

<p align="center">
  <img src="https://i.pinimg.com/736x/c4/ec/2d/c4ec2d9ebc2c7f70a6cb68e9082fdf04.jpg" width="400" alt="Cybersecurity GIF">
</p>


---

```asm
section .data
    profile_info db "Hi, I'm Abderrahmane Sebban", 10
    role_info    db "Cybersecurity Enthusiast & CTF Player", 10
    focus_info   db "Binary Exploitation | Reverse | Cryptography", 10
    tools_title  db "Languages and Tools:", 10
    tools_list   db "C / C++ | x86-64 ASM | Python | Bash", 10

section .text
    global _start

_start:
    mov esi, profile_info
    call print_line

    mov esi, role_info
    call print_line

    mov esi, focus_info
    call print_line

    mov esi, tools_title
    call print_line

    mov esi, tools_list
    call print_line

    mov eax, 1
    xor ebx, ebx
    int 0x80

print_line:
.loop:
    mov al, [esi]
    cmp al, 10
    je .newline

    mov eax, 4
    mov ebx, 1
    mov ecx, esi
    mov edx, 1
    int 0x80

    inc esi
    jmp .loop

.newline:
    mov eax, 4
    mov ebx, 1
    mov ecx, esi
    mov edx, 1
    int 0x80

    inc esi
    ret
