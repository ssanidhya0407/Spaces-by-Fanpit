# 🚀 Fanpit - Event Management Platform

A modern, full-stack event management platform built with Next.js, TypeScript, and Firebase. Organizers can create and manage events, while users can discover, register, and attend events.

## ✨ Features

- **🎯 Event Management**: Create, edit, and manage events with rich details
- **📍 Location Services**: Interactive map integration with latitude/longitude coordinates
- **👥 Speaker Management**: Add multiple speakers with profile images
- **🏷️ Tagging System**: Categorize events with multiple tags and categories
- **📱 Responsive Design**: Modern UI with Tailwind CSS and mobile-first approach
- **🔐 Authentication**: Secure user authentication with role-based access control
- **📊 Real-time Updates**: Live data synchronization with Firebase
- **🖼️ Image Uploads**: Firebase Storage integration for event posters and speaker images

## 🛠️ Tech Stack

- **Frontend**: Next.js 15.4.6 (App Router) + TypeScript
- **Styling**: Tailwind CSS v4
- **Backend**: Firebase (Firestore, Authentication, Storage)
- **State Management**: React Query (TanStack Query)
- **Forms**: React Hook Form + Zod validation
- **UI Components**: Lucide React icons
- **Notifications**: React Hot Toast
- **Date Handling**: date-fns

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v18.17 or higher)
- **npm** (v9.0 or higher)
- **Git**
- **Firebase account** and project

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd Fanpit
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Environment Configuration

Create a `.env.local` file in the root directory with your Firebase configuration:

```env
# Firebase Configuration
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key_here
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=your_measurement_id
```

### 4. Firebase Setup

#### Create Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project or select existing one
3. Enable the following services:
   - **Authentication** (Google, Email/Password)
   - **Firestore Database**
   - **Storage**

#### Configure Authentication
1. In Firebase Console → Authentication → Sign-in method
2. Enable **Google** and **Email/Password** providers
3. Add your domain to authorized domains

#### Configure Firestore
1. Go to Firestore Database → Rules
2. Set up security rules for your collections
3. Create the following collections:
   - `events` - for event data
   - `users` - for user profiles
   - `registrations` - for event registrations

#### Configure Storage
1. Go to Storage → Rules
2. Set up rules for image uploads
3. Create `event_images/` folder for event posters

### 5. Run the Development Server

```bash
npm run dev
```

The application will be available at `http://localhost:3000` (or the next available port).

## 📁 Project Structure

```
src/
├── app/                    # Next.js App Router pages
│   ├── (public)/          # Public routes
│   ├── events/            # Event-related pages
│   ├── login/             # Authentication pages
│   ├── organizer/         # Organizer-only pages
│   ├── profile/           # User profile pages
│   ├── globals.css        # Global styles
│   ├── layout.tsx         # Root layout
│   └── providers.tsx      # Context providers
├── components/            # Reusable UI components
│   ├── EventCard.tsx      # Event display component
│   ├── EventGrid.tsx      # Events grid layout
│   ├── LocationPicker.tsx # Map location picker
│   ├── Navbar.tsx         # Navigation component
│   ├── PosterUpload.tsx   # Image upload component
│   ├── RoleGate.tsx       # Role-based access control
│   ├── SpeakerManager.tsx # Speaker management
│   └── TagSelector.tsx    # Tag selection component
├── hooks/                 # Custom React hooks
│   ├── auth.ts            # Authentication hooks
│   └── events.ts          # Event-related hooks
├── lib/                   # Utility libraries
│   └── firebase.ts        # Firebase configuration
├── services/              # API services
│   └── events.ts          # Event CRUD operations
├── types/                 # TypeScript type definitions
│   └── models.ts          # Data models and interfaces
└── constants/             # Application constants
```

## 🎯 Available Scripts

```bash
# Development
npm run dev          # Start development server with Turbopack
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint

# Package Management
npm install          # Install dependencies
npm update           # Update dependencies
```

## 🌐 Application Routes

| Route | Description | Access |
|-------|-------------|---------|
| `/` | Public events grid | Public |
| `/events/[id]` | Event details and registration | Public |
| `/login` | Authentication and role selection | Public |
| `/profile` | User profile and registrations | Authenticated users |
| `/organizer/new` | Create new event | Organizers only |
| `/organizer/events` | My active events | Organizers only |
| `/organizer/events/[id]/registrations` | Event registrations | Organizers only |

## 🔧 Development

### Adding New Features
1. Create components in `src/components/`
2. Add types in `src/types/models.ts`
3. Implement services in `src/services/`
4. Create hooks in `src/hooks/`
5. Add pages in `src/app/`

### Code Style
- Use TypeScript for all new code
- Follow Next.js App Router conventions
- Use Tailwind CSS for styling
- Implement proper error handling
- Add TypeScript interfaces for all data structures

### Testing
```bash
# Run type checking
npm run build

# Run linting
npm run lint
```

## 🚀 Deployment

### Build for Production
```bash
npm run build
```

### Deploy to Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Deploy to Other Platforms
- **Netlify**: Build command: `npm run build`, Publish directory: `.next`
- **Firebase Hosting**: Use Firebase CLI for deployment
- **AWS Amplify**: Connect repository and set build settings

## 🔒 Security Considerations

- Firebase security rules are configured for data protection
- User authentication is required for protected routes
- Role-based access control for organizer features
- Input validation with Zod schemas
- Secure file uploads with Firebase Storage

## 🐛 Troubleshooting

### Common Issues

1. **Firebase Configuration Error**
   - Verify all environment variables are set correctly
   - Check Firebase project settings and API keys

2. **Build Errors**
   - Ensure Node.js version is 18.17+
   - Clear `.next` folder and `node_modules`
   - Run `npm install` again

3. **Authentication Issues**
   - Verify Firebase Auth is enabled
   - Check authorized domains in Firebase Console
   - Ensure Google OAuth is configured

4. **Database Connection Issues**
   - Verify Firestore rules allow read/write operations
   - Check Firebase project billing status

### Getting Help
- Check the console for error messages
- Verify Firebase Console for service status
- Review environment variable configuration
- Check network tab for API call failures

## 📚 Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [React Query Documentation](https://tanstack.com/query/latest)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Support

For support and questions:
- Create an issue in the repository
- Check the troubleshooting section above
- Review Firebase Console for service status

---

**Happy coding! 🎉**