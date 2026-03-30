# Windows Server Active Directory Lab

## Descripción

Este proyecto consiste en la implementación de una infraestructura básica de red empresarial utilizando Windows Server, Active Directory, usuarios, grupos, unidades organizativas y un servidor de archivos con permisos por departamentos.

El objetivo es simular el entorno de una empresa donde los usuarios se organizan por departamentos y tienen acceso únicamente a sus carpetas correspondientes.

---

## Tecnologías utilizadas

* Windows Server
* Active Directory Domain Services
* DNS Server
* PowerShell
* Windows 10/11 cliente
* NTFS Permissions
* File Server

---

## Estructura del dominio

Se ha creado el dominio:

```
empresa.local
```

Estructura de Unidades Organizativas:

```
empresa.local
└── Empresa
    ├── Ventas
    ├── IT
    └── Direccion
```

---

## Usuarios creados

| Usuario | Departamento |
| ------- | ------------ |
| juan    | Ventas       |
| ana     | Ventas       |
| pedro   | IT           |
| laura   | IT           |
| jefe    | Direccion    |

---

## Grupos de seguridad

| Grupo         | Departamento |
| ------------- | ------------ |
| GRP_Ventas    | Ventas       |
| GRP_IT        | IT           |
| GRP_Direccion | Direccion    |

Los usuarios se han añadido a sus respectivos grupos para la gestión de permisos.

---

## Servidor de archivos

Se ha creado un servidor de archivos con la siguiente estructura:

```
C:\Empresa
    ├── Ventas
    ├── IT
    └── Direccion
```

Recurso compartido:

```
\\SERVIDOR\Empresa
```

---

## Permisos NTFS

| Carpeta   | Grupo con acceso |
| --------- | ---------------- |
| Ventas    | GRP_Ventas       |
| IT        | GRP_IT           |
| Direccion | GRP_Direccion    |

La carpeta principal **Empresa** tiene permisos de lectura para *Domain Users* y cada subcarpeta tiene permisos de modificación solo para su grupo correspondiente.

---

## Cliente unido al dominio

Un equipo cliente Windows se ha unido al dominio **empresa.local** y se ha comprobado el inicio de sesión con usuarios del dominio.

Comprobación en CMD:

```
whoami
empresa\juan
```

---

## Comandos PowerShell utilizados

Listar usuarios:

```
Get-ADUser -Filter *
```

Listar grupos:

```
Get-ADGroup -Filter *
```

Ver miembros de un grupo:

```
Get-ADGroupMember GRP_Ventas
```

---

## Pruebas de acceso

Se han realizado pruebas de acceso al servidor de archivos:

| Usuario | Ventas | IT | Direccion |
| ------- | ------ | -- | --------- |
| juan    | ✔      | ✘  | ✘         |
| pedro   | ✘      | ✔  | ✘         |
| jefe    | ✘      | ✘  | ✔         |

---

## Capturas del proyecto

(Incluir aquí las capturas)

* Configuración IP servidor
* Roles instalados
* Active Directory
* Unidades Organizativas
* Usuarios
* Grupos
* Permisos NTFS
* Cliente unido al dominio
* Acceso a carpetas compartidas
* Comandos PowerShell

---

## Autor

Lorenzo León
Proyecto de laboratorio de administración de sistemas con Windows Server y Active Directory.
