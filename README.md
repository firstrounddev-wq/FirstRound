# Async Interview Frontend

A Next.js application for conducting video interviews with candidates.

## Prerequisites

- Node.js 18+ 
- npm or yarn
- Backend API server running (see backend documentation)

## Environment Setup

1. Copy the environment template:
```bash
cp .env.example .env.local
```

2. Configure your environment variables in `.env.local`:
```bash
# Backend API URL - Replace with your deployed backend URL
NEXT_PUBLIC_API_URL=http://localhost:8080

# For production, use your Railway/deployed backend URL:
# NEXT_PUBLIC_API_URL=https://your-backend-app-production.up.railway.app
```

## Getting Started

First, install dependencies:

```bash
npm install
# or
yarn install
```

Then, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## API Configuration

The application uses the `NEXT_PUBLIC_API_URL` environment variable to connect to your backend.

### For Development:
- Set `NEXT_PUBLIC_API_URL=http://localhost:8080` (or your local backend port)

### For Production:
- Set `NEXT_PUBLIC_API_URL=https://your-backend-domain.com`
- Ensure your backend has CORS configured for your production domain

## Features

- ✅ Video interview recording
- ✅ Multiple question support
- ✅ Real-time video upload
- ✅ Interview kit management
- ✅ Authentication via Supabase
- ✅ Responsive design

## Troubleshooting

### Video Upload Issues
1. Check browser console for network errors
2. Verify `NEXT_PUBLIC_API_URL` is correctly set
3. Ensure backend is running and accessible
4. Check browser permissions for camera/microphone

### API Connection Issues
1. Verify backend is running on the specified URL
2. Check CORS configuration in backend
3. Inspect Network tab in browser DevTools
4. Check environment variables are loaded correctly

## Development Notes

- All API calls are centralized in `src/lib/api-config.ts`
- Video recording uses the native MediaRecorder API
- FormData is used for file uploads (don't manually set Content-Type)
- Error handling includes network timeout and connectivity checks

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
