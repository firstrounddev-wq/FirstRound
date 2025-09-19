# Deployment Guide for FirstRound Async Interview Platform

## Production Deployment Checklist

### 1. Environment Variables Configuration

Before deploying to Vercel, you MUST update these environment variables:

#### In Vercel Dashboard:
1. Go to your project settings
2. Navigate to "Environment Variables" 
3. Add these variables:

```
# Supabase Configuration (keep these as-is)
NEXT_PUBLIC_SUPABASE_URL=https://gfqwodjhousrtmiqruhs.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImdmcXdvZGpob3VzcnRtaXFydWhzIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTc5MjAyNzAsImV4cCI6MjA3MzQ5NjI3MH0.RB2hwF8bujkLgduUiPMx3nCmplsqU08TpZ2kpKtlZZA

# R2 Configuration (keep these as-is)
R2_ENDPOINT=https://pub-7a770dc720464207bd89f96f920901cc.r2.dev
R2_BUCKET_NAME=async-interview-mvp-snoof

# API Configuration (UPDATE THESE!)
NEXT_PUBLIC_API_BASE_URL=https://your-railway-backend.railway.app
NEXT_PUBLIC_SITE_URL=https://your-vercel-app.vercel.app
```

### 2. Backend API Requirements

Your Railway backend MUST:

1. **Accept HTTPS requests** from your Vercel domain
2. **Configure CORS** to allow requests from your Vercel app:
   ```
   Access-Control-Allow-Origin: https://your-vercel-app.vercel.app
   Access-Control-Allow-Methods: GET, POST, OPTIONS
   Access-Control-Allow-Headers: Content-Type, Authorization, User-Agent
   ```

3. **Support these endpoints**:
   - `GET /kits/:id` - Get interview kit details
   - `POST /kits` - Create new interview kit (requires auth)
   - `GET /submissions` - Get submissions (requires auth)
   - `POST /upload` - Upload video responses

### 3. CORS Configuration

Make sure your Railway backend has CORS configured for:
- Your Vercel production domain: `https://your-vercel-app.vercel.app`
- Your custom domain (if using one)

### 4. TLS/SSL Configuration

- Railway should automatically provide HTTPS
- Ensure all API calls use HTTPS in production
- Verify SSL certificates are valid

### 5. Testing Production Deployment

After deployment, test:

1. **Interview Link Loading**: `/interview/[kitId]` should fetch and display questions
2. **Video Upload**: Candidates should be able to record and submit videos
3. **Dashboard Access**: Recruiters should be able to view kits and submissions
4. **Authentication**: Supabase auth should work correctly

### 6. Common Issues and Solutions

#### Issue: "Interview Not Found" on valid links
- **Cause**: Backend not accessible from Vercel
- **Solution**: Check NEXT_PUBLIC_API_BASE_URL points to Railway backend

#### Issue: Video upload fails
- **Cause**: CORS not configured or backend errors
- **Solution**: Check backend logs and CORS configuration

#### Issue: Authentication errors
- **Cause**: Supabase configuration or environment variables
- **Solution**: Verify Supabase environment variables are correct

### 7. Monitoring and Debugging

1. **Vercel Function Logs**: Check for server-side errors
2. **Browser Console**: Check for client-side errors
3. **Railway Logs**: Monitor backend API responses
4. **Network Tab**: Verify API calls are reaching the backend

### 8. Performance Optimization

- Images and videos are served from Cloudflare R2
- API responses are not cached (`cache: 'no-store'`)
- Static assets are automatically optimized by Vercel

## Quick Reference URLs

Replace these with your actual URLs:
- Frontend: `https://your-vercel-app.vercel.app`
- Backend: `https://your-railway-backend.railway.app`
- R2 Storage: `https://pub-7a770dc720464207bd89f96f920901cc.r2.dev`