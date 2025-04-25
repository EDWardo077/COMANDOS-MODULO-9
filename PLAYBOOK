Claro, aquí tienes un ejemplo de **playbook de Ansible** que sigue tu estructura y realiza dos tareas principales:

1. Crear un usuario.
2. Descargar una herramienta (por ejemplo, `htop` como herramienta de monitoreo, puedes cambiarla por la que desees).

```yaml
# crear_usuario_descargar_herramienta.yml
- name: Crear un usuario y descargar una herramienta
  hosts: linux
  become: yes
  tasks:
    - name: Crear usuario "nuevo_usuario"
      user:
        name: nuevo_usuario
        shell: /bin/bash
        state: present
        create_home: yes

    - name: Asegurarse de que los repositorios estén actualizados
      apt:
        update_cache: yes

    - name: Instalar herramienta "htop"
      apt:
        name: htop
        state: present
```

🔧 **Personalización:**
- Cambia `nuevo_usuario` por el nombre que necesites.
- Cambia `htop` por la herramienta que desees instalar (`nmap`, `curl`, `git`, etc.).

¿Quieres que añada también configuración de sudo para el usuario?


Perfecto. Aquí tienes el **playbook actualizado** para crear un usuario y descargar e instalar la herramienta `bashtop`:

```yaml
# crear_usuario_instalar_bashtop.yml
- name: Crear un usuario y descargar e instalar bashtop
  hosts: linux
  become: yes
  tasks:
    - name: Crear usuario "nuevo_usuario"
      user:
        name: nuevo_usuario
        shell: /bin/bash
        state: present
        create_home: yes

    - name: Actualizar caché de APT
      apt:
        update_cache: yes

    - name: Instalar bashtop
      apt:
        name: bashtop
        state: present
```

📌 **Notas importantes:**
- `bashtop` está disponible en los repositorios de Ubuntu 20.04 y superiores. Si estás usando una versión más antigua, podrías necesitar instalarlo desde GitHub o Snap.
- Si `bashtop` no está en los repos oficiales de tu sistema, avísame y te doy un playbook alternativo que lo instala desde su fuente en GitHub.

¿En qué sistema operativo estás corriendo esto (por ejemplo, Ubuntu 20.04, Debian, etc.)?


Perfecto, si deseas clonar el repositorio de `bashtop` desde GitHub en lugar de instalarlo vía `apt`, aquí tienes el playbook actualizado que:

1. Crea un usuario.  
2. Clona el repositorio `bashtop` desde GitHub.  
3. Ejecuta la instalación de `bashtop`.

```yaml
# crear_usuario_instalar_bashtop_git.yml
- name: Crear un usuario y clonar bashtop desde GitHub
  hosts: linux
  become: yes
  tasks:
    - name: Crear usuario "nuevo_usuario"
      user:
        name: nuevo_usuario
        shell: /bin/bash
        state: present
        create_home: yes

    - name: Instalar dependencias necesarias (git, make, etc.)
      apt:
        name:
          - git
          - make
          - gcc
          - g++
          - cmake
        state: present
        update_cache: yes

    - name: Clonar repositorio bashtop en /opt/bashtop
      git:
        repo: https://github.com/aristocratos/bashtop.git
        dest: /opt/bashtop
        version: master

    - name: Ejecutar script de instalación de bashtop
      shell: |
        make install
      args:
        chdir: /opt/bashtop
```

✅ Esto clonará `bashtop` en `/opt/bashtop` y ejecutará su instalación con `make install`.

¿Quieres que `bashtop` sea accesible globalmente para todos los usuarios (añadirlo al PATH si es necesario)?
