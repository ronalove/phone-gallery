# Phone Gallery 📱

A modern, glassmorphism-styled web application to track and showcase your personal phone collection history. Built with Next.js 14, TypeScript, and SQLite.

![Phone Gallery](https://img.shields.io/badge/Next.js-14-black?style=flat-square&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=flat-square&logo=typescript)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=flat-square&logo=sqlite)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker)

## ✨ Features

- **📱 Phone Collection Management**: Track all phones you've owned with detailed metadata
- **🎨 Modern Glassmorphism UI**: Beautiful dark theme with glass effects and neon glows
- **📊 Statistics Dashboard**: Visualize your phone history with interactive charts
- **🌍 Bilingual**: Full French/English language support with toggle switcher
- **🖼️ Image Storage**: Upload and store phone images directly in SQLite as base64
- **⚙️ Admin Interface**: Easy-to-use CRUD interface for managing your collection
- **🐳 Docker Ready**: Full Docker support with persistent volume for database
- **📱 Responsive**: Works seamlessly on desktop and mobile devices

## 🛠️ Tech Stack

- **Frontend**: Next.js 14 (App Router), React 18, TypeScript
- **Styling**: Tailwind CSS with custom glassmorphism utilities
- **UI Components**: shadcn/ui (Radix UI primitives)
- **Database**: SQLite with better-sqlite3
- **Theming**: next-themes with dark mode support
- **Icons**: Lucide React
- **Deployment**: Docker with docker-compose

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm
- Docker and Docker Compose (for containerized deployment)

### Installation

#### Development with npm

```bash
# Clone the repository
git clone https://github.com/ronalove/phone-gallery.git
cd phone-gallery

# Navigate to source directory
cd src

# Install dependencies
npm install

# Start development server
npm run dev
```

The application will be available at `http://localhost:3000`.

#### Production with Docker Compose

Create a `docker-compose.yml` file:

```yaml
services:
  phone-gallery:
    image: ghcr.io/ronalove/phone-gallery:latest
    container_name: phone-gallery-app
    ports:
      - "3000:3000"
    volumes:
      - phone-data:/app/data
    environment:
      - NODE_ENV=production
      - PORT=3000
      - HOSTNAME=0.0.0.0
      - DB_PATH=/app/data/phones.db
    restart: unless-stopped
    networks:
      - phone-gallery-network

volumes:
  phone-data:
    driver: local

networks:
  phone-gallery-network:
    driver: bridge
```

Then run:

```bash
# Start the application
docker-compose up -d

# View logs
docker-compose logs -f

# Stop the application
docker-compose down
```

### Building from Source with Docker

```bash
# Build the image
docker build -t phone-gallery .

# Run the container
docker run -p 3000:3000 -v phone-data:/app/data phone-gallery
```

## 📁 Project Structure

```
phone-gallery/
├── src/                        # Source code directory
│   ├── app/                    # Next.js app directory
│   │   ├── admin/              # Admin interface
│   │   ├── api/                # API routes
│   │   └── page.tsx            # Main page
│   ├── components/             # React components
│   │   ├── ui/                 # shadcn/ui components
│   │   ├── phone-gallery.tsx   # Main gallery component
│   │   └── phone-statistics.tsx # Statistics dashboard
│   ├── contexts/               # React contexts
│   │   └── language-context.tsx # i18n context
│   ├── lib/                    # Utility libraries
│   │   ├── db.ts               # SQLite database setup
│   │   ├── i18n.ts             # Translations
│   │   └── migrate-*.ts        # Migration scripts
│   ├── types/                  # TypeScript types
│   └── data/                   # SQLite database (gitignored)
├── docker-compose.yml          # Docker Compose configuration
├── Dockerfile                  # Docker image definition
└── README.md                   # This file
```

## 🎯 Usage

### Main Gallery

Browse your phone collection with:
- **Gallery View**: Grid of phone cards with images, ownership dates, and sentiment indicators
- **Statistics View**: Detailed analytics about your collection

### Admin Panel

Access the admin interface at `/admin` to:
- **Add New Phones**: Upload images and fill in phone details
- **Edit Existing Entries**: Update any phone information
- **Delete Phones**: Remove phones from your collection
- **Manage Images**: Upload images directly (stored as base64 in SQLite)

### Data Model

Each phone entry includes:
- **Brand**: Manufacturer (Apple, Samsung, etc.)
- **Model Name**: Specific model (iPhone 16 Pro, Galaxy S24, etc.)
- **Year Start**: When you started using it
- **Year End**: When you stopped (null if current)
- **Liked**: Whether you liked the phone (green cards)
- **Kept**: Whether you still physically own it
- **Image**: Phone image (stored as base64)

## 🎨 Design Features

### Glassmorphism

The app uses custom CSS utilities for glass effects:
- `.glass` - Light glass effect
- `.glass-strong` - Stronger glass effect
- `.glass-liked` - Green tint for liked phones
- `.glass-disliked` - Red tint for disliked phones

### Neon Glows

Hover effects with colored glows:
- `.neon-cyan` - Cyan glow
- `.neon-purple` - Purple glow
- `.neon-pink` - Pink glow
- `.neon-green` - Green glow (liked phones)
- `.neon-red` - Red glow (disliked phones)

## 🌍 Internationalization

The app supports French and English with a language toggle button. Default language is French.

Translations are managed in `src/lib/i18n.ts` and can be easily extended to support additional languages.

## 📦 Environment Variables

```bash
NODE_ENV=production        # Environment mode
PORT=3000                 # Application port
HOSTNAME=0.0.0.0          # Bind hostname
DB_PATH=/app/data/phones.db  # SQLite database path
```

## 🔧 Development

```bash
# Run development server
cd src
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linter
npm run lint
```

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**Ronan Lamour**

- GitHub: [@ronalove](https://github.com/ronalove)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

---

Built with ❤️ using Next.js and modern web technologies
