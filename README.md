# 🐄 Asoganaderos Facatativá — SIS-INFO v1.0

> Sistema de Información Seguro para la Gestión de Datos Ganaderos  
> Proyecto Final · Ingeniería de Datos e Inteligencia Artificial · USTA  
> Autor: **Wilmer Sneider Merchan Uribe**

---

## 📁 Estructura del proyecto

```
asoganaderos/
│
├── login.html              ← Pantalla de acceso (ya funciona sin backend)
├── dashboard.html          ← Panel principal (próximo módulo)
├── asoganaderos_datos.sql  ← Base de datos completa para MySQL/XAMPP
└── README.md               ← Este archivo
```

---

## 🚀 Opción 1 — Ver el login YA (sin instalar nada)

### GitHub Pages (gratis, 2 minutos)

1. Ve a [github.com](https://github.com) y crea una cuenta si no tienes
2. Clic en **New repository**
3. Nombre: `asoganaderos-sisinfo`
4. Marca **Public** ✅
5. Clic en **Create repository**
6. Arrastra y suelta `login.html` y `README.md` al repositorio
7. Ve a **Settings → Pages → Branch: main → Save**
8. Tu sitio estará en:  
   `https://TU_USUARIO.github.io/asoganaderos-sisinfo/login.html`

> ✅ El `login.html` funciona **100% sin servidor** — es HTML puro.  
> El SQL se conecta cuando tengas PHP + MySQL (XAMPP).

---

## 🖥️ Opción 2 — Con XAMPP (backend real)

### Instalación paso a paso

```
1. Descarga XAMPP: https://www.apachefriends.org
2. Instala y abre XAMPP Control Panel
3. Inicia Apache y MySQL (botón Start)
4. Copia la carpeta del proyecto a:
      Windows: C:\xampp\htdocs\asoganaderos\
      Mac/Linux: /opt/lampp/htdocs/asoganaderos/
5. Abre phpMyAdmin: http://localhost/phpmyadmin
6. Clic en "Nueva base de datos" → nombre: asoganaderos_facatativa
7. Pestaña "Importar" → selecciona asoganaderos_datos.sql → Continuar
8. Abre en el navegador: http://localhost/asoganaderos/login.html
```

---

## 👤 Cuentas de acceso (demo)

### 🔐 Administradores — requieren llave única adicional

| Usuario | Correo | Contraseña | Llave única |
|---------|--------|------------|-------------|
| Wilmer Merchan | `wilmer.merchan@asoganaderos.com` | `WilmerAdmin2024!` | `eakuQB4TvpO4iR3pF6dbN1EGs+hH0fs4` |
| Admin Sistema  | `admin.sistema@asoganaderos.com`  | `SistemaAdmin2024!` | `9O9NzgbihuG9yTBx1CRpzxGss82q8ZGR` |

> ⚠️ Las llaves de admin son secretas. En producción se guardan como hash bcrypt en la BD.  
> Nunca compartirlas públicamente en un sistema real.

### 🩺 Veterinarios (color verde)

| Correo | Contraseña |
|--------|------------|
| `juan.garcia@asoganaderos.com`  | `JuanVet2024!` |
| `carlos.vega@asoganaderos.com`  | `CarlosVet2024!` |

### 👨‍💼 Empleados (color azul)

| Correo | Contraseña |
|--------|------------|
| `maria.lopez@asoganaderos.com` | `MariaEmp2024!` |
| `luisa.mora@asoganaderos.com`  | `LuisaEmp2024!` |

### 👨‍🌾 Ganaderos (color naranja) — registro público disponible

| Correo | Contraseña |
|--------|------------|
| `carlos.hernandez@gmail.com` | `CarlosGan2024!` |
| `luis.martinez@gmail.com`    | `LuisGan2024!`  |

> Los ganaderos pueden registrarse solos desde el formulario de login.  
> Los demás roles (admin, vet, empleado) solo los asigna el administrador.

---

## 🔒 Seguridad implementada

| Mecanismo | Descripción |
|-----------|-------------|
| **bcrypt (cost 12)** | Contraseñas hasheadas, nunca en texto plano |
| **Llave única admin** | Segunda capa de autenticación solo para administradores |
| **AES-256-CBC** | Cifrado de datos sensibles: cédulas, teléfonos, correos |
| **Control de roles** | Cada rol ve y puede hacer solo lo que le corresponde |
| **Auditoría** | Registro de todas las acciones: quién, qué, cuándo, desde dónde |
| **Sesiones PHP** | `session_start()` + `$_SESSION` para mantener el acceso activo |

---

## 🗄️ Base de datos — resumen

| Tabla | Registros | Descripción |
|-------|-----------|-------------|
| `roles` | 4 | admin, veterinario, empleado, ganadero |
| `usuarios` | 8 | Con hashes bcrypt + llave admin |
| `ganaderos` | 30 | Productores de la región Orinoquia |
| `fincas` | 100 | 68 pequeñas · 22 medianas · 10 grandes |
| `ganado` | ~3.655 | Carga 0.2–1.2 animales/ha según tipo |
| `vacunacion` | ~574 | Fiebre Aftosa, Brucela, Carbón, etc. |
| `produccion` | 600 | 50 fincas × 12 meses (leche, carne, ingresos COP) |
| `atenciones` | 20 | Interacciones ganadero ↔ empleado |
| `auditoria` | 12 | Log de acciones del sistema |

---

## 🧱 Módulos del sistema

```
Módulo 1 — Login + Llave Admin      ✅ Listo
Módulo 2 — Dashboard principal      🔨 En desarrollo
Módulo 3 — Registro de ganado       🔨 En desarrollo
Módulo 4 — Vacunación y sanidad     📋 Pendiente
Módulo 5 — Producción               📋 Pendiente
Módulo 6 — Atenciones ganadero      📋 Pendiente
Módulo 7 — Auditoría                📋 Pendiente
Módulo 8 — Reportes                 📋 Pendiente
```

---

## 🛠️ Tecnologías

| Parte | Tecnología |
|-------|------------|
| Frontend | HTML5 + CSS3 + JavaScript |
| Backend (pendiente) | PHP 8+ |
| Base de datos | MySQL 8 / MariaDB |
| Servidor local | XAMPP |
| Encriptación | bcrypt · AES-256-CBC · openssl_encrypt |
| Control de versiones | Git + GitHub |
| Hosting gratuito | GitHub Pages (solo frontend) |

---

## 📌 Cómo conectar el login con PHP (próximo paso)

Cuando tengas XAMPP funcionando, el archivo `login.php` va así:

```php
<?php
session_start();
require_once 'config/db.php'; // conexión PDO

$correo = $_POST['correo'];
$pass   = $_POST['contrasena'];
$rol    = $_POST['rol'];

$stmt = $pdo->prepare(
    "SELECT u.*, r.nombre_rol FROM usuarios u
     JOIN roles r ON u.id_rol = r.id_rol
     WHERE u.correo = ? AND u.activo = 1"
);
$stmt->execute([$correo]);
$usuario = $stmt->fetch();

if ($usuario && password_verify($pass, $usuario['contrasena'])) {
    // Verificar llave si es admin
    if ($rol === 'admin') {
        $llave = $_POST['llave_admin'];
        if (!password_verify($llave, $usuario['llave_admin'])) {
            die(json_encode(['error' => 'Llave de administrador incorrecta']));
        }
    }
    // Registrar en auditoría
    $ip = $_SERVER['REMOTE_ADDR'];
    $pdo->prepare(
        "INSERT INTO auditoria (id_usuario, usuario_nom, accion, modulo, ip_cliente)
         VALUES (?,?,?,?,?)"
    )->execute([$usuario['id_usuario'], $usuario['nombre'],
                'Inicio de sesión', 'auth', $ip]);

    $_SESSION['id_usuario'] = $usuario['id_usuario'];
    $_SESSION['nombre']     = $usuario['nombre'];
    $_SESSION['rol']        = $usuario['nombre_rol'];
    header('Location: dashboard.php');
    exit;
} else {
    header('Location: login.html?error=1');
    exit;
}
?>
```

---

*Proyecto académico — Universidad Santo Tomás — 2025*
