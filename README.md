# Heyzik - Modern Portfolio Website

A clean, minimalist portfolio website built with Vue 3 and Vite. Showcases data engineering projects with an elegant design and interactive features.

![Portfolio Preview](app/public/avatar.png)

## ✨ Features

- 🎨 Clean and minimalist design with white theme
- 📱 Fully responsive layout (mobile-first design)
- 🔄 Smooth transitions and hover animations
- 📑 Three main sections:
  - **Home**: Personal introduction with social links
  - **Portfolio**: Interactive project showcase with modal popups
  - **Contact**: Simple contact form
- 🖼️ Portfolio modal view with project details and CTA buttons
- 🔗 GitHub and live demo links for each project
- 💫 Hidden scrollbars for clean UI
- 🚀 Fast loading with optimized assets

## 🛠️ Technology Stack

- **Frontend Framework:** Vue 3 with Composition API
- **Build Tool:** Vite
- **Styling:** 
  - Custom CSS with modern features
  - Roboto font family
  - CSS Grid and Flexbox layouts
  - Smooth animations and transitions
- **Data Management:** YAML for portfolio data
- **Code Quality:**
  - ESLint for code linting
  - Clean, maintainable component structure

## 🚀 Quick Start

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone https://github.com/zikranazir/heyzik.git
cd heyzik/app
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

5. Build for production:
```bash
npm run build
```

## 🎯 Project Structure

```
app/
├── public/              # Static assets
│   ├── avatar.png      # Profile image
│   └── favicon.ico     # Site favicon
├── src/
│   ├── assets/         # Stylesheets
│   │   ├── base.css    # Base styles
│   │   └── homepage.css # Homepage specific styles
│   ├── components/     # Vue components
│   │   ├── HomePage.vue     # Landing page component
│   │   ├── PortfolioPage.vue # Portfolio showcase with modals
│   │   ├── ContactPage.vue   # Contact form
│   │   └── icons/      # Icon components
│   ├── data/           # Data files
│   │   └── portfolio.yaml # Portfolio projects data
│   ├── App.vue         # Root component with navigation
│   └── main.js         # Application entry point
└── index.html          # HTML entry point
```

## 🔧 Configuration

- **Vite Configuration:** See `vite.config.js` for build and development settings
- **Portfolio Data:** Edit `src/data/portfolio.yaml` to update projects
- **Contact Email:** Messages are sent to `zikranazir@protonmail.com`
- **Development Tools:** Optimized for modern development workflow

## 📱 Responsive Design

The website features a mobile-first responsive design:

- **Desktop (1024px+)**: Full navigation, grid layouts, optimal spacing
- **Tablet (768px - 1023px)**: Adapted layouts with adjusted spacing
- **Mobile (320px - 767px)**: Single column, touch-friendly interface
- **Very Small Screens (320px and below)**: Optimized for compact displays

## 🎨 Design Features

- **Clean White Theme**: Minimalist design with white backgrounds
- **Roboto Typography**: Modern, readable font family
- **Hidden Scrollbars**: Clean UI without visible scrollbars
- **Smooth Animations**: Hover effects and transitions
- **Modal Interactions**: Detailed project views with CTAs
- **Fixed Navigation**: Always accessible navigation bar

## 📊 Portfolio Projects

The portfolio showcases data engineering and analytics projects:

- **Sales Analytics Dashboard**: Real-time visualization with Python & Streamlit
- **Customer Segmentation Model**: ML-powered marketing insights
- **Data Pipeline Automation**: ETL processes with Apache Airflow
- **Predictive Analytics Tool**: Time series forecasting
- **Real-time Data Streaming**: IoT data processing with Kafka
- **Business Intelligence Suite**: Comprehensive BI solution

Each project includes:
- Detailed descriptions
- Technology stacks
- GitHub repository links
- Live demo links

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/zikranazir/heyzik/issues).

## 📝 License

This project is [MIT](https://choosealicense.com/licenses/mit/) licensed.

## 👤 Author

**Zikra Wahyudi**
- GitHub: [@zikranazir](https://github.com/zikranazir)
- LinkedIn: [zikra-wahyudi](https://www.linkedin.com/in/zikra-wahyudi/)
- Medium: [@zikranazir](https://medium.com/@zikranazir)
- Email: zikranazir@protonmail.com

## 🚀 Deployment

This project can be easily deployed to various platforms:

- **Netlify**: Connect your GitHub repo for automatic deployments
- **Vercel**: Import project for seamless deployment
- **GitHub Pages**: Use GitHub Actions for CI/CD
- **Firebase Hosting**: Deploy with Firebase CLI

Build command: `npm run build`  
Output directory: `dist`

---

⭐️ If you like this project, give it a star on GitHub!