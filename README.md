# Cantina Escolar - Frontend Telegram Mini App

Este repositorio contiene la interfaz Web / Mini App de Telegram para el sistema de pedidos de **Cantina Escolar**. Está desarrollada con HTML5, CSS3 y JavaScript vanilla, integrada directamente con el **Telegram Web Apps SDK**.

---

## 🚀 Características Principales

- **Integración con Telegram Web App:** Utiliza el SDK oficial (`telegram-web-app.js`) para adaptarse a la apariencia nativa de Telegram (modo claro/oscuro dinámico).
- **Catálogo Interactivo de Productos:** Filtrado por categorías (*Comidas*, *Bebidas*, *Snacks*).
- **Carrito de Compras en Tiempo Real:** Control mediante botones de incremento/decremento (`+` / `-`) con cálculo automático de totales.
- **Campo de Observaciones:** Permite incluir especificaciones adicionales para el pedido (ej. "sin salsa", "entregar a estudiante X").
- **Botón Principal Nativo (`MainButton`):** Sincronizado dinámicamente con el total del pedido y la cantidad de productos seleccionados.
- **Envío de Datos en Formato JSON:** Transmite la orden estructurada al bot de Telegram mediante `Telegram.WebApp.sendData()`.
- **Modo Fallback Web:** Compatible para pruebas directas en navegadores convencionales fuera de la app de Telegram.
- **Haptic Feedback:** Respuesta táctil en dispositivos móviles al interactuar con el menú.

---

## 📂 Estructura del Proyecto

```text
frontend_bot_telegram_cantina/
├── index.html     # Aplicación completa (HTML, Estilos CSS y Lógica JavaScript)
└── README.md      # Documentación del proyecto
```

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 & CSS3:** Diseño responsivo con variables CSS ligadas a los temas de Telegram (`var(--tg-theme-*)`).
- **JavaScript (Vanilla ES6+):** Manipulación del DOM, estado del carrito y lógica de negocio.
- **Telegram Web App SDK v6+:** Integración con la plataforma de Telegram.

---

## 📄 Estructura del Payload Enviado al Bot

Al hacer clic en **Confirmar Pedido**, la Mini App genera y transmite un objeto JSON estructurado:

```json
{
  "type": "CANTINA_ORDER",
  "timestamp": "2026-10-11T12:00:00.000Z",
  "order": {
    "items": [
      {
        "id": "emp_carne",
        "name": "Empanada de Carne",
        "unitPrice": 1.5,
        "quantity": 2,
        "subtotal": 3.0
      },
      {
        "id": "jugo_durazno",
        "name": "Jugo Natural de Durazno",
        "unitPrice": 1.0,
        "quantity": 1,
        "subtotal": 1.0
      }
    ],
    "totalAmount": 4.0,
    "currency": "USD",
    "totalItems": 3,
    "notes": "Empanada bien tostada por favor"
  }
}
```

---

## 💻 Cómo Probar y Desplegar

### 1. Prueba Local
Abre el archivo `index.html` directamente en tu navegador web. El sistema detectará que no está dentro de Telegram y activará el modo de contingencia (*fallback*), permitiendo probar la interfaz y ver la simulación del envío de datos.

### 2. Despliegue para Telegram
1. Publica el archivo `index.html` en un servidor web con HTTPS (ej. **GitHub Pages**, **Vercel**, **Netlify**).
2. En Telegram, contacta a [@BotFather](https://t.me/BotFather).
3. Configura un Web App o Mini App vinculando la URL HTTPS del proyecto en tu Bot.

---

## 📝 Licencia

Este proyecto está disponible bajo la licencia MIT.
