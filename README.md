# Zikra Wahyudi - Portfolio Website

A modern, responsive portfolio website built with Vue 3 and Vite. Features a clean minimalist design showcasing data engineering projects with interactive modals and smooth user experience.

## 🚀 Features

- **Responsive Design** - Mobile-first approach with breakpoints for all devices
- **Interactive Portfolio** - Modal popups with project details and CTA buttons
- **Modern UI** - Clean white theme with Poppins font and smooth animations
- **Fast Loading** - Optimized with Vite for quick build and deployment
- **GitHub Pages Ready** - Automated deployment with GitHub Actions

## 🛠️ Tech Stack

- **Vue 3** - Progressive JavaScript framework
- **Vite** - Next generation frontend build tool
- **CSS3** - Modern styling with responsive design
- **YAML** - Data storage for portfolio projects
- **GitHub Actions** - Automated CI/CD pipeline

## 📁 Project Structure

```
├── README.md
├── app/
│   ├── index.html          # Main HTML template
│   ├── package.json        # Dependencies and scripts
│   ├── vite.config.js      # Vite configuration
│   ├── public/
│   │   ├── CNAME          # Custom domain configuration
│   │   ├── favicon_1.ico  # Website favicon
│   │   └── portfolio.yaml # Portfolio data
│   └── src/
│       ├── App.vue        # Main application component
│       ├── main.js        # Application entry point
│       ├── assets/
│       │   ├── base.css   # Base styles and variables
│       │   └── styles.css # Component-specific styles
│       └── components/
│           ├── HomePage.vue     # Landing page component
│           ├── PortfolioPage.vue # Portfolio showcase
│           └── ContactPage.vue   # Contact form
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/zikranazir/heyzik.git
   cd heyzik/app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Build for production**
   ```bash
   npm run build
   ```

## 🌐 Deployment

This project is configured for automatic deployment to GitHub Pages using GitHub Actions.

### Custom Domain Setup
The website is deployed to a custom domain (`heyzik.xyz`) configured via the `CNAME` file in the public folder.

### Deployment Process
1. Push changes to the `main` branch
2. GitHub Actions automatically builds and deploys the site
3. Changes are live within minutes

## 📞 Contact

**Zikra Wahyudi**  
- GitHub: [@zikranazir](https://github.com/zikranazir)
- LinkedIn: [zikra-wahyudi](https://www.linkedin.com/in/zikra-wahyudi/)
- Medium: [@zikranazir](https://medium.com/@zikranazir)
- Email: zikranazir@gmail.com

## 📄 License

This project is open source and available under the [MIT License](LICENSE)..