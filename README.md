# Steven Madasu's AI Portfolio Assistant

A production-grade AI-powered chatbot that answers questions about Steven Madasu's background, experience, projects, and expertise through an intelligent conversation interface. Built with modern web technologies and powered by Supabase for data persistence and Edge Functions for AI integration.

## Overview

This application serves as an interactive portfolio companion that provides visitors with detailed, accurate information about Steven's professional journey, technical skills, and entrepreneurial ventures. The chatbot leverages PDF document extraction and intelligent content retrieval to deliver contextually relevant answers.

## Features

- **Intelligent Chatbot**: AI-powered assistant that answers questions based on verified portfolio documents
- **PDF Knowledge Base**: Automatic text extraction and indexing from PDF documents
- **Admin Dashboard**: Secure interface for managing portfolio content and analytics
- **Analytics Tracking**: Real-time Q&A analytics with feedback mechanisms
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Row Level Security**: Comprehensive database security with fine-grained access control

## Tech Stack

### Frontend
- **React 18** - UI framework
- **TypeScript** - Type-safe development
- **Vite** - Lightning-fast build tool
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Icon library

### Backend & Infrastructure
- **Supabase** - PostgreSQL database with real-time capabilities
- **Supabase Edge Functions** - Serverless functions for PDF extraction and chat processing
- **OpenAI API** - GPT-3.5-turbo for intelligent responses

### DevOps
- **Vite** - Modern bundler and dev server
- **TypeScript** - Static type checking
- **ESLint** - Code quality assurance

## Getting Started

### Prerequisites
- Node.js 16+ and npm
- Supabase account and project
- OpenAI API key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Stevenmadasu/portfolio-chatbot.git
   cd portfolio-chatbot
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env.local
   ```

   Edit `.env.local` with your Supabase credentials:
   ```
   VITE_SUPABASE_URL=https://your-project.supabase.co
   VITE_SUPABASE_ANON_KEY=your-anon-key-here
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

   The app will be available at `http://localhost:5173`

### Building for Production

```bash
npm run build
```

The optimized production build will be output to the `dist/` directory.

## Project Structure

```
src/
├── components/          # React components
│   ├── admin/          # Admin dashboard components
│   ├── auth/           # Authentication components
│   ├── ChatHeader.tsx  # Chat interface header
│   ├── ChatInput.tsx   # Chat message input
│   ├── ChatMessage.tsx # Chat message display
│   └── Navigation.tsx  # App navigation
├── hooks/              # Custom React hooks
│   └── useChat.ts      # Chat interaction logic
├── lib/                # Utilities and configuration
│   ├── database.types.ts # Auto-generated Supabase types
│   └── supabase.ts     # Supabase client setup
├── pages/              # Page components
│   ├── AdminPage.tsx   # Admin dashboard
│   └── ChatPage.tsx    # Chat interface
├── utils/              # Helper functions
│   └── contextRetrieval.ts # Knowledge base querying
├── App.tsx             # Main app component
├── main.tsx            # Entry point
└── index.css           # Global styles

supabase/
├── functions/          # Edge Functions
│   ├── chat/          # Chat processing function
│   ├── create-admin/  # Admin setup function
│   └── extract-pdf/   # PDF text extraction function
└── migrations/        # Database migrations
```

## Key Features Explained

### Chat System
The chatbot processes user queries by:
1. Extracting relevant keywords from the question
2. Searching the knowledge base for matching content
3. Calculating relevance scores
4. Passing relevant context to OpenAI's GPT-3.5-turbo
5. Returning an intelligent, contextual response

### PDF Knowledge Base
- PDFs are automatically processed using the `extract-pdf` Edge Function
- Text is extracted and stored in the `knowledge_base` table
- Content is indexed and searchable through the chat interface
- Admin users can upload new documents through the dashboard

### Admin Dashboard
Secure interface for:
- Managing knowledge base documents
- Viewing Q&A analytics
- Managing website links
- Creating admin users

## Database Schema

### Core Tables
- `knowledge_base` - Stores PDF content and metadata
- `website_links` - Portfolio links and resources
- `chat_history` - Chat message history
- `chat_analytics` - Q&A performance tracking

All tables have Row Level Security (RLS) enabled with appropriate access policies.

## Security

- **Row Level Security**: Fine-grained access control on all database tables
- **Environment Secrets**: Sensitive configuration stored in `.env` files
- **API Key Protection**: OpenAI keys and Supabase credentials never exposed to client
- **Admin Authentication**: Secure admin verification through Supabase Auth
- **CORS Headers**: Proper cross-origin resource sharing configuration on Edge Functions

## Environment Variables

Create a `.env.local` file with:

```
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key-here
```

Additional configuration can be added for:
- `OPENAI_API_KEY` (configured in Supabase Edge Function secrets)
- `SUPABASE_SERVICE_ROLE_KEY` (for admin operations)

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Create production build
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run typecheck` - Check TypeScript types

### Code Style

The project uses ESLint for code quality. Configuration is in `eslint.config.js`.

## Performance Optimizations

- **Lazy Loading**: Components and routes are code-split for faster initial load
- **Database Indexes**: Strategic indexes on frequently queried columns
- **RLS Query Optimization**: Subquery patterns for optimal performance at scale
- **CSS Purging**: Tailwind CSS removes unused styles in production

## Contributing

This is a personal portfolio project. For suggestions or improvements, feel free to open issues.

## License

This project is proprietary and maintained by Steven Madasu.

## Contact

- **GitHub**: [@Stevenmadasu](https://github.com/Stevenmadasu)
- **Email**: stevenmadasu@gmail.com
- **LinkedIn**: [Steven Madasu](https://linkedin.com/in/steven-madasu-b54293221)

## Acknowledgments

Built with:
- [Supabase](https://supabase.com) for backend infrastructure
- [React](https://react.dev) for UI framework
- [Vite](https://vitejs.dev) for build tooling
- [OpenAI](https://openai.com) for AI capabilities
- [Tailwind CSS](https://tailwindcss.com) for styling
