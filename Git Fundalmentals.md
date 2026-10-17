# Git Fundamentals

Curso GitHub Foundation (Microsoft) · GH-900T00
https://learn.microsoft.com/es-es/training/courses/gh-900t00

## Índice
1. [Arquitectura y conceptos base](#arquitectura-y-conceptos-base)
2. [Flujo de trabajo local](#flujo-de-trabajo-local)
3. [Historial de Git](#historial-de-git)
4. [Guía rápida de comandos](#guía-rápida-de-comandos)
5. [Árbol genealógico](#árbol-genealógico)
6. [Tipos de ramas en Git Flow](#tipos-de-ramas-en-git-flow)
7. [GitHub: issues y pull requests](#github-issues-y-pull-requests)
8. [Productos de GitHub](#productos-de-github)
9. [Escaneo de código](#escaneo-de-código)
10. [Gestión de repositorios](#gestión-de-repositorios)
11. [Gestión de vulnerabilidades](#gestión-de-vulnerabilidades)
12. [Tipos de autenticación](#tipos-de-autenticación)
13. [2FA y SAML](#2fa-y-saml)
14. [Roles y permisos](#roles-y-permisos)
15. [Autenticación y autorización](#autenticación-y-autorización)
16. [Estados de una solicitud de cambios](#estados-de-una-solicitud-de-cambios)
17. [Extras](#extras)

## Arquitectura y conceptos base
- **VCS** — control de versiones; copias local y en nube.
- **Git** — VCS distribuido para colaborar en paralelo.
- **Área de trabajo (Workspace)** — carpeta del proyecto.
- **Repositorio** — archivos del directorio `.git`.
- **Hash** — detecta cambios comparando bits.
- **Objeto** — Git tiene 4: blob, tree, commit y tag.
- **Commit** — versión del árbol, ya visible para otros.
- **Rama (Branch)** — versión alterna de `main` para cambios propios.
- **HEAD** — la última confirmación generada.
- **Remote** — apodo del repositorio remoto en GitHub.
- **Origin** — remote para subir/bajar cambios entre Git y GitHub.

Ejercicio 1:
https://github.com/ffernacu/skills-introduction-to-git/issues/1

## Flujo de trabajo local
- **Directorio de trabajo** — archivos del proyecto.
- **Área de preparación (Staging)** — archivos en modificación.
- **Repositorio local** — commits ya confirmados.

## Historial de Git
Cada commit contiene:
- **ID hash** — referencia en el historial.
- **Commit padre** — commit anterior; forma una cadena.
- **Autor** — quién hizo los cambios.
- **Marca de tiempo** — cuándo se aplicaron.
- **Mensaje** — descripción de los cambios.

Conceptos:
- **main** — rama principal (antes master).
- **merge** — fusión de cambios entre ramas.

## Guía rápida de comandos

### git log --oneline
- **Propósito:** resumir el historial.
- **Funcionamiento:** lista los commits, uno por línea.
```bash
git log --oneline
```

### git checkout <commit_id>
- **Propósito:** viajar en el tiempo en el proyecto.
- **Funcionamiento:** mueve HEAD a un commit pasado para revisarlo.
```bash
git checkout <commit_id>
```

### git log --all --graph --oneline
- **Propósito:** ver commits de todos los branches.
- **Funcionamiento:** dibuja un mapa con líneas, un commit por línea.
```bash
git log --all --graph --oneline
```

### git diff
- **Propósito:** diferencias entre área de trabajo y staging.
- **Funcionamiento:** cambios actuales vs. lo guardado con `git add`.
```bash
git diff
```

### git diff --staged
- **Propósito:** diferencias entre staging y el commit anterior.
- **Funcionamiento:** lo que entrará en el próximo commit.
```bash
git diff --staged
```

### git diff HEAD~1
- **Propósito:** diferencias entre el commit actual y el anterior.
- **Funcionamiento:** compara HEAD contra el commit inmediato anterior.
```bash
git diff HEAD~1
```

## Árbol genealógico
De Ing. de Sistemas hasta Git:
- Ingeniería de Sistemas
  - Ingeniería de Software
    - Admin. de la Configuración (SCM)
      - Control de Versiones
        - Control de Versiones Distribuido
          - Git

De mayor a menor:
- **Ing. de Sistemas** — modela sistemas complejos (hardware, software, personas y procesos).
- **Ing. de Software** — sistemas informáticos y ciclo de vida del código.
- **SCM** — controla la evolución del software.
- **Control de Versiones** — registra el historial de cambios.
- **Control de Versiones Distribuido** — cada dev tiene copia completa del historial.

## Tipos de ramas en Git Flow
- **master** — código listo para producción.
- **develop** — desarrollo más reciente (próxima versión).
- **feature/\*** — nuevas funcionalidades; nace y se fusiona en `develop`.
- **release/\*** — prepara una versión de producción desde `develop`.
- **hotfix/\*** — revisiones urgentes; nace de `master`.

## GitHub: issues y pull requests
- **Issues** — temas relativos al código.
- **Discusiones** — foro colaborativo.
- **Pull request** — solicitud de integración de cambios.
- **GitHub** — plataforma en la nube que hospeda repositorios Git.

## Productos de GitHub

### Cuentas
- **Enterprise (cuenta)** — nivel corporativo; seguridad, políticas y facturación de varias orgs.
- **Organización** — espacio de equipo; roles y permisos.
- **Personal** — identidad individual del desarrollador.

### Planes
- **Free** (personal/org) — seguridad básica y alertas; sin revisiones avanzadas en repos privados.
- **Pro** (personal) — revisores obligatorios, ramas protegidas y Code Owners.
- **Team** (org) — accesos por grupos, borradores de PR y revisiones por equipos.
- **Enterprise (plan)** — reglas globales, SSO y protección avanzada de despliegues.

### Facturación
- **Suscripción/licencia** — GitHub Pro, Copilot (tokens limitados).
- **Por consumo** — GitHub Actions, Copilot, Codespaces.

### Secretos cifrados
- Variable de entorno confidencial para pipelines (conexiones, tokens).
- Se protege con criptografía asimétrica.

## Escaneo de código
- **CodeQL** — escaneo de GitHub (basado en OWASP Top 10).
  - Por defecto: Security and quality → code scanning default.
  - Avanzada: Security and quality → code scanning advance.
  - Copilot Autofix: se habilita en ambos casos.
  - **Findings** — vulnerabilidades; se ven en code scanning → Open / Closed.
- **Copilot**
  - Chat — consultor de código.
  - Plan agente — diseño, ejecución y preview.
  - Agente — implementación de código.
- **Codespaces** — entorno de desarrollo virtual sin servidor.
- **Markdown** — lenguaje simplificado de texto.

## Gestión de repositorios
- **InnerSource** — colaboración en repos internos (opuesto a open source).

### Visibilidad
- **Público** — cualquiera en internet.
- **Interno** — solo miembros de la empresa (ideal InnerSource).
- **Privado** — solo el dueño e invitados.

### Niveles de permiso de repositorio
- **Lectura (Reading)** — ver repositorios (devs de otros equipos).
- **Triaje** — crear/asignar/cerrar issues y PRs; no aprueba ni fusiona (QAs).
- **Escritura (Writing)** — push de cambios; aprueba PRs según el caso (devs).
- **Mantenimiento** — aprueba PRs, protege ramas y administra config (SSR, LT).
- **Administración** — habilita acceso, elimina o transfiere el repo (Infra).

### Plantillas de repositorio
- **Readme** — manual del proyecto: propósito y expectativas.
- **Contributing** — guía de modificación para colaboradores.
- **CodeOwners** — devs que revisan y aprueban PRs.
- **Issue Template** — estructura para nuevos issues.
- **Pull Request** — plantilla de aprobación de cambios.

- **Readiness assessment** — adopción de InnerSource; aumenta solicitudes de corrección.
- **Supply chain** — conjunto de librerías.

## Gestión de vulnerabilidades
- **Dependency graph** — origen de las librerías.
  - Dependency review.
- **Dependabot** — escanea librerías vulnerables; genera recomendaciones y PRs.
  - Dependabot alerts.
  - Dependabot updates.
- **GitHub Advisory Database** — vulnerabilidades próximas y sus correcciones.
  - https://github.com/advisories

## Tipos de autenticación
- Clave y contraseña
- Tokens de acceso
- Clave SSH
- Claves de implementación
- **OTP** — código de un solo uso, vida configurable.
- **TOTP** — OTP de vida corta (segundos), vía app.

## 2FA y SAML
Cumplimiento de 2FA:
- GitHub Team
- GitHub Enterprise Cloud
- Usuarios administrados por empresa (EMU)
- GitHub Enterprise Server (GHE): vía Active Directory
- **SAML** — SSO con tokens intermedios entre aplicaciones.

## Roles y permisos

### Roles a nivel de equipo
- **Team Member** — recibe acceso a los repos asignados.
- **Team Maintainer** — administra el grupo; agrega/quita personas.

### Permisos de organización
- **Miembro** — crea y administra repos y equipos (Enterprise Member).
- **Moderador** — bloquea colaboradores, limita interacción y oculta comentarios.
- **Admin. de facturación** — ve y edita la facturación.
- **Admin. de seguridad** — administra alertas y config de seguridad.
- **Colaborador externo** — acceso a repos; no es miembro de la org.

### Permisos de empresa
- **Propietario** — control total: admins, orgs, políticas y facturación.
- **Miembro** — mismas capacidades que en la organización.
- **Admin. de facturación** — solo facturación y sus admins.
- **Colaborador invitado** — acceso limitado (solo usuarios administrados).

## Autenticación y autorización
Reducen ataques por credenciales y mejoran el inicio de sesión.
- **Passkey** — inicio sin contraseña, ligado a dispositivo físico; resiste phishing.
- **WebAuthn** — biometría y tokens de hardware (YubiKey).

### EMU (usuarios administrados por empresa)
En GitHub Enterprise Cloud la autenticación pasa por el IdP:
- Restringe el acceso a cuentas administradas por la empresa.
- Control central sobre identidad, credenciales y sesión.

GitHub quita solo a miembros de la organización que no se autentican:
- **Miembros de la organización** — expulsados de inmediato de la lista interna.
- **Miembros de empresa** — externos y admins de facturación pierden acceso al fallar SAML.

IdP admitidos: Okta, Microsoft Entra ID, Google Workspace.

## Estados de una solicitud de cambios
- **Borrador (Draft)** — no se fusiona; no pide revisión automática.
- **Abierta (Open)** — activa y sin fusionar; admite commits y revisión.
- **Cerrada (Closed)** — se cierra sin fusionar; útil si ya no se necesitan los cambios.
- **Fusionada (Merged)** — cambios combinados con la rama base.
- **Outdated** — código obsoleto; sugiere cambio en files changed.

## Extras
- **Git Blame** — historial de commits de un archivo.
