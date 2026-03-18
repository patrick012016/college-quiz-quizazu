
<div align="center">
  <img width="201" height="232" alt="Quizazu" src="https://github.com/user-attachments/assets/9fc465b9-da37-4954-9da7-b0cf8b38663c" />
  <h1>Quizazu | College quiz</h1><div align="center">

![.NET](https://img.shields.io/badge/.NET_6.0-5C2D91?style=for-the-badge&logo=.net&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)
![Azure](https://img.shields.io/badge/Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![SignalR](https://img.shields.io/badge/SignalR-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
<br>
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)


</div>
</div>
Quizazu is a client-server application designed for creating, managing, and participating in real-time multiplayer quizzes.  The system consists of a web application that handles both quiz management and gameplay, and a native Android application serving as a dedicated gameplay client.

## Table of contents
* [Features](#features)
* [Gallery](#gallery)
* [Tech stack](#tech-stack)
* [Third-party libraries](#third-party-libraries)
* [Infrastructure & deployment](#infrastructure--deployment)
* [Basic requirements & setup](#basic-requirements--setup)
* [Authors](#authors)
* [License](#license)

## Gallery
**Home page**
 <img width="1588" height="797" alt="zdj1" src="https://github.com/user-attachments/assets/c2cd129d-4d12-4ec8-b0d3-47c08b1f03d0" />

**Player gameplay view**
<img width="1189" height="788" alt="zdj2" src="https://github.com/user-attachments/assets/b0d07934-3b52-46c3-9e9f-91c220de6001" />

**Host lobby view**
<img width="1184" height="655" alt="zdj3" src="https://github.com/user-attachments/assets/26c90bbf-3202-4823-a23e-2c5600ab495c" />


## Features
### Gameplay & real-time synchronization
*  Real-time bidirectional communication during active quiz sessions using SignalR.
*  Support for five distinct question types: True/False, Single Choice (4 options), Multiple Choice (4 options), Single Choice (6 options), and a Range Slider.
*  Time-based scoring algorithm calculating points based on answer speed and correctness.
*  Host lobby management features, including generating QR codes for joining, toggling answer visibility, and kicking/banning participants.

### User management & security
*  JWT-based authentication for the WebAPI.
*  Account registration with email verification requiring confirmation within 48 hours.
*  Secure password policies enforcing 8-25 characters, uppercase, lowercase, numbers, and special characters.
*  Automated password reset workflow via email tokens.

### Monetization & subscriptions
*  Integration with the PayU API for processing subscription payments.
*  Three-tier account authorization logic (Standard, Gold, Platinum) restricting access to specific question types based on the user's active tier.
*  Promotional coupon system allowing users to redeem codes for temporary subscription upgrades.

### Administration panel
*  Statistical dashboard monitoring users, quizzes, coupons, and active subscriptions.
*  CRUD operations for user and administrator accounts, including permanent or temporary account suspension.
*  Content moderation tools allowing administrators to block or delete user-generated quizzes.
*  Management of subscription pricing and discount parameters.

## Tech stack

**Clients**:
* **Web application:**
    * ASP.NET Core Razor Pages (server-side rendering for static pages)
    * React.js (client-side rendering for dynamic content)
    * HTML5, CSS3, JavaScript, Bootstrap
* **Mobile application:** 
    * Native Android in Java (see [GitHub repository](https://github.com/patrick012016/college-quiz-quizazu-mobile-app))

**Server**:
* ASP.NET Core C# MVC
* ASP.NET Core WebAPI (REST endpoints, WebSockets via SignalR)

## Third-party libraries
* **SignalR** - full-duplex WebSockets communication technology
* **React** - client-side rendering technology
* **JWT** - WebAPI authentication technology
* **Bootstrap** - CSS/JS library
* **Bootstrap email, Liquid** - email templates
* **anime.js** - web animations
* **CropperJS** - image resizer JS library
* **noUiSlider** - range sliders
* **RetroNotify** - JavaScript toasts library
* **Webpack, Babel** - JavaScript bundler and transpiler
* **Swashbuckle AspNetCore Swagger** - C# API documentation
* **SkiaSharp, SkiaSharp SVG, SkiaSharp QRCode** - C# image processing, QR Codes
* **PayU Client** - C# payments client
* **Entity Framework Core** - C# ORM database system
* **FluentFTP** - C# FTP file transferring
* **FluentEmail, FluentEmail Liquid** - C# mail sender
* **DotNetEnv** - C# environment variables loader

## Infrastructure & deployment
* **Microsoft Azure** - main server and SignalR broker provider
* **MyDevil** - MySQL database and static content data storage
* **Forpsi** - domain provider and SMTP server

## Basic requirements & setup
Before you begin, ensure you have met the following local development requirements:
* **.NET SDK 6.0** (C# 10)
* **Node.js** (v16.x or newer recommended) and **npm**
* **MySQL Server** (v8.0.29 or compatible)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/patrick012016/college-quiz-quizazu.git
   cd college-quiz-quizazu
   ```
2. **Configure environment variables:**
   To run the application locally, the following environment variables must be configured in the `.env` file at the root of your project. 

> [!NOTE]
You can use the provided `.env.sample` file as a template.

```env
# Database
MY_SEQUEL_CONNECTION=[connection string]

# SMTP Server
SMTP_HOST=[SMTP provider address]
SMTP_PASSWORD=[email password]

# PayU Integration
CLIENT_ID=[PayU client ID]
CLIENT_SECRET=[PayU secret]

# JWT Authentication
JWT_SECRET=[token secret]
JWT_ISSUER=[token issuer]

# SFTP (Static Content)
SFTP_HOST=[SFTP address]
SFTP_USERNAME=[SFTP login]
SFTP_PASSWORD=[SFTP password]
SFTP_HREF=[main server url]
```
> [!TIP]
> SFTP usage can be bypassed for local development by setting `"ExternalContentServerActive": false` in the `appsettings.json` file.


3. **Install client-side dependencies:**
   Navigate to the directory containing your React/JavaScript files and install the required packages:
   ```bash
   npm install
   ```

4. **Apply database migrations:**
   Ensure your MySQL server is running, then update your database schema using Entity Framework Core:
   ```bash
   dotnet ef database update
   ```

5. **Build and run the application:**
   ```bash
   dotnet run
   ```
> [!NOTE]
>  The application API and Web UI will now be available on your localhost (check `launchSettings.json` for the exact port).


## Authors

- [@Lettulouz](https://www.github.com/Lettulouz) - Leader
- [@Milosz08](https://www.github.com/Milosz08) - Lead developer, game session designer, WebSockets communication, client-side rendering
- [@patrick012016](https://www.github.com/patrick012016) - Mobile app development, core system support ([GitHub repository](https://github.com/patrick012016/college-quiz-quizazu-mobile-app))
- [@tentegess](https://www.github.com/tentegess) - Admin panel
- [@NicoMroo](https://www.github.com/NicoMroo) - Graphics
- [@kBaginskik](https://www.github.com/kBaginskik) - Game session with [@Milosz08](https://www.github.com/Milosz08)
- [@crucialis](https://www.github.com/crucialis) - Mobile app deploy

## App testers

- [@Arek2017](https://github.com/Arek2017)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

