# Deploying to Cloudflare Pages

This guide will help you deploy your Expense Tracker application to Cloudflare Pages.

## Prerequisites

- GitHub repository with your code (✅ Already done!)
- Cloudflare account (free tier available)
- Supabase project set up (if using cloud storage)

## Deployment Steps

### 1. Create Cloudflare Account

1. Go to [Cloudflare Pages](https://pages.cloudflare.com/)
2. Sign up for a free account or log in
3. Click **"Create a project"**

### 2. Connect Your GitHub Repository

1. Click **"Connect to Git"**
2. Authorize Cloudflare to access your GitHub account
3. Select your repository: **`shaz290/expense-tracker`**
4. Click **"Begin setup"**

### 3. Configure Build Settings

Use these exact settings:

**Framework preset:** `Next.js`

**Build command:**
```bash
npm run build
```

**Build output directory:**
```
.next
```

**Root directory:** `/` (leave as default)

**Node version:** `18` or higher

### 4. Add Environment Variables

Click **"Environment variables"** and add your Supabase credentials:

| Variable Name | Value |
|--------------|-------|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Your Supabase anon key |

> **Note:** Get these from your Supabase dashboard → Settings → API

### 5. Deploy

1. Click **"Save and Deploy"**
2. Wait 2-3 minutes for the build to complete
3. Your app will be live at: `https://expense-tracker-xxx.pages.dev`

## Post-Deployment

### Custom Domain (Optional)

1. Go to your Cloudflare Pages project
2. Click **"Custom domains"**
3. Add your domain (e.g., `expenses.yourdomain.com`)
4. Follow DNS setup instructions

### Update Supabase URL Whitelist

1. Go to Supabase Dashboard → Authentication → URL Configuration
2. Add your Cloudflare Pages URL to **Site URL**
3. Add to **Redirect URLs**: `https://your-app.pages.dev/**`

### Enable Analytics (Optional)

Cloudflare Pages includes free analytics:
1. Go to your project → Analytics
2. View traffic, performance, and usage stats

## Automatic Deployments

Every time you push to your `main` branch on GitHub, Cloudflare will automatically:
- Build your app
- Run tests (if configured)
- Deploy the new version
- Keep previous deployments for rollback

## Troubleshooting

### Build Fails

**Error:** `Module not found`
- **Solution:** Make sure all dependencies are in `package.json`
- Run `npm install` locally to verify

**Error:** `Environment variable not found`
- **Solution:** Add environment variables in Cloudflare Pages settings
- Redeploy after adding variables

### App Loads but Features Don't Work

**Supabase connection fails:**
- Verify environment variables are set correctly
- Check Supabase URL whitelist includes your Cloudflare domain
- Check browser console for CORS errors

**localStorage not working:**
- This is normal - localStorage works fine on Cloudflare Pages
- Make sure you're not in incognito/private mode

## Performance Tips

1. **Enable Cloudflare CDN** (automatic)
2. **Use Cloudflare Images** for any uploaded images
3. **Enable Auto Minify** in Cloudflare dashboard
4. **Use Cloudflare Analytics** to monitor performance

## Cost

- **Cloudflare Pages:** FREE (unlimited bandwidth, 500 builds/month)
- **Supabase:** FREE tier (500MB database, 50,000 monthly active users)
- **Custom Domain:** FREE if you already own one

## Next Steps

After deployment:
1. Test all features on the live site
2. Share the URL with users
3. Set up custom domain (optional)
4. Monitor analytics and usage
5. Enable Cloudflare security features

## Support

- [Cloudflare Pages Docs](https://developers.cloudflare.com/pages/)
- [Next.js on Cloudflare](https://developers.cloudflare.com/pages/framework-guides/nextjs/)
- [Supabase Docs](https://supabase.com/docs)

---

**Your app is now live and accessible from anywhere! 🎉**
