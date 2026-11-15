# My_first_web
# EcoAI — Artificial Intelligence in Sustainability Web Portal
**Unit 7175: Web Design and Programming — Assessment 3**  
**University of Canberra — Faculty of Science and Technology**  
**Candidate:** Student ID: u3306446  

---

## 📖 Project Overview

**EcoAI** is a responsive full-stack **ASP.NET Core MVC** web application designed and engineered to satisfy all requirements of **Assessment 3 for Unit 7175: Web Design and Programming** at the **University of Canberra**.

The website focuses on the **AI in Sustainability** theme, specifically investigating how deep learning, atmospheric telemetry, smart grids, and computer vision empower **Climate Prediction**, **Energy Optimisation**, and **Smart Agriculture**.

---

## 🎯 Topic & Thematic Scope: AI in Sustainability

In accordance with the assessment specification, the portal explores three core pillars of artificial intelligence in environmental sustainability:
1. **Climate Prediction:** High-performance neural networks model complex atmospheric physics, forecast severe weather anomalies, and track global greenhouse gas concentrations with unmatched precision (e.g., GraphCast by Google DeepMind, ClimaX by Microsoft Research).
2. **Energy Optimisation:** Machine learning algorithms dynamically balance fluctuating renewable supplies, forecast peak loads on electrical grids, and reduce thermal data center power consumption (e.g., DeepMind Autonomous Cloud Cooling, AutoGrid Virtual Power Plants).
3. **Smart Agriculture:** Computer vision and predictive IoT sensors optimize water usage, reduce chemical pesticide runoff via precision spraying, and maximize crop yields sustainably (e.g., John Deere See & Spray, Climate LLC FieldView).

---

## 📋 Comprehensive Requirements Traceability Matrix

| Requirement # | Assessment Specification | Implementation Details in EcoAI |
| :--- | :--- | :--- |
| **1. Full-Width Layout** | The layout takes up the entire space with zero blank space on all sides and between elements. | `body, html` reset to `margin: 0; padding: 0; width: 100%; overflow-x: hidden;`. All sections and containers span edge-to-edge with 0px gaps. |
| **2. Required Web Pages** | • 2 pages in `Views/Home/`: `Index.cshtml`, `Contact.cshtml`<br>• 5 pages in `Views/AIImages/`: `Create.cshtml`, `Details.cshtml`, `Delete.cshtml`, `Edit.cshtml`, `Index.cshtml`<br>• `_Layout.cshtml`<br>• Register & Login pages<br>• 1 additional creative page | • `Views/Home/Index.cshtml` & `Contact.cshtml` implemented.<br>• Full CRUD in `Views/AIImages/` matching model on Page 22.<br>• `_Layout.cshtml` includes header, nav, and footer.<br>• `AccountController` + `Views/Account/Register.cshtml` & `Login.cshtml`.<br>• `Views/Home/EcoCalculator.cshtml` interactive creative page linked from menu and footer. |
| **3. Font Imports & Styling** | External CSS only (`site.css`). Anton, Montserrat, Lato, Oxygen, and Niconne fonts loaded. | Google Fonts `<link>` imported in `_Layout.cshtml`. Zero inline styles (`style="..."`) and zero internal `<style>` tags anywhere in `.cshtml` files. |
| **4. Viewport Scroll Blocks** | 3 blocks appear ONLY when fully in viewport, disappear when scrolled out. | Driven by `IntersectionObserver` in `wwwroot/js/site.js` toggling `.is-visible` on `.viewport-block` elements. |
| **5. Tool Examples Hover** | 2 examples per block. Image preview fades out/in on hover to reveal description. | Implemented via CSS transitions in `site.css` with external hyperlinks opening official tool documentation in a new tab. |
| **6. Upload Section** | Login prompt for visitors; upload button linking to `/AIImages/Create` for authenticated users. | Razor conditional `@if (SignInManager.IsSignedIn(User))` handles role-based display in `Views/Home/Index.cshtml`. |
| **7. Bottom Gallery Grid** | Images sorted by Like count descending. Up to 6 items/row desktop, 3 tablet, 2 mobile. 2-second hover fade. | Responsive CSS Grid in `site.css`. Hover effect transitions image opacity over 2 seconds (`transition: opacity 2s ease`). Card clicks anchor to `/AIImages/Index#image-{id}`. |
| **8. Role-Based Access** | • Visitor: read-only, no action buttons.<br>• Member: Create + single Like per session.<br>• Admin: Like + Edit + Delete + Details. | Handled via ASP.NET Core Identity roles (`Admin`, `Member`) and session tracking (`LikedAIImageIds`) with `[Authorize]` attributes in `AIImagesController`. |
| **9. Contact Page** | 3 content columns (Contact Us, About Us, Copyright) with Niconne headings and yellow text. | Responsive Bootstrap grid with `border: 1px solid white; box-shadow: 10px 10px 0px 0px #f8f6b0;`, yellow Arial body text, and Niconne subheadings. Strictly anonymous. |
| **10. Parallax Scrolling** | Fixed parallax background across pages. | Uses `background-image: url('../images/sustainability_bg.jpg'); background-attachment: fixed; background-size: cover;`. |

---

## 🛠️ Technology Stack

* **Framework:** ASP.NET Core MVC (Targeting .NET 10.0 / 8.0)
* **Language:** C#
* **Database & ORM:** SQLite (`EduAIWeb.db`) with Entity Framework Core
* **Authentication & Authorization:** ASP.NET Core Identity with role-based authorization (`Admin`, `Member`) and Session State
* **Frontend:** Razor Views (`.cshtml`), Bootstrap 5, Font Awesome 6, Bootstrap Icons, Google Fonts
* **Styling & Scripts:** Pure external CSS (`wwwroot/css/site.css`) and modular vanilla JavaScript (`wwwroot/js/site.js`)

---

## 🔐 Default Test Credentials

| Role | Username / Email | Password | Allowed Capabilities |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@asp.net` | `Admin@123` | Upload AI Images, Like (1x/session), Edit Image, Delete Image, Access Details |
| **Member** | `member@asp.net` | `Member@123` | Upload AI Images, Like (1x/session) |
| **Visitor** | *(Unauthenticated)* | *(N/A)* | Browse Home, View Gallery (Read-only, no action buttons), View Contact & EcoCalculator |

---

## 🚀 How to Run the Project

```bash
# 1. Build the application
dotnet build

# 2. Run the application
dotnet run --urls "http://127.0.0.1:5100"
```

Navigate to `http://127.0.0.1:5100` in Google Chrome or Microsoft Edge.
