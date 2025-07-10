# 🚀 Deployment Guide

This guide covers deploying your Hedera NFT Overlay Tool to production. We recommend Vercel for its simplicity, performance, and generous free tier.

## 🌟 Recommended: Vercel Deployment

Vercel offers the best experience for deploying this application with zero configuration required.

### Why Vercel?

- ✅ **Free tier** with generous limits
- ✅ **Automatic SSL** certificates
- ✅ **Global CDN** for fast loading
- ✅ **GitHub integration** for automatic deployments
- ✅ **Custom domains** supported
- ✅ **Scales automatically** as your app grows

### Prerequisites

- GitHub account
- Vercel account (free) - [Sign up here](https://vercel.com)
- Your code pushed to a GitHub repository

### Step-by-Step Deployment

#### 1. Prepare Your Repository

Ensure your code is ready:

```bash
# Test your build locally
npm run build

# Commit and push your changes
git add .
git commit -m "Ready for deployment"
git push origin main
```

#### 2. Connect to Vercel

1. Visit [vercel.com](https://vercel.com) and sign in
2. Click **"New Project"**
3. Import your GitHub repository
4. Vercel will automatically detect it's a Vite project

#### 3. Configure Build Settings

Vercel should auto-detect these settings, but verify:

- **Framework Preset**: Vite
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Install Command**: `npm install`

#### 4. Environment Variables (Optional)

If you're using environment variables, add them in Vercel:

1. Go to your project settings
2. Navigate to **Environment Variables**
3. Add your variables:
   - `VITE_WALLETCONNECT_PROJECT_ID`
   - `VITE_APP_NAME`
   - `VITE_APP_URL`

#### 5. Deploy

Click **"Deploy"** and wait for the build to complete (usually 1-2 minutes).

#### 6. Custom Domain (Optional)

1. Go to your project settings
2. Navigate to **Domains**
3. Add your custom domain
4. Follow DNS configuration instructions

### Automatic Deployments

Once connected, Vercel will automatically deploy:
- ✅ Every push to your main branch
- ✅ Pull request previews
- ✅ Rollback capabilities

## 🔧 Alternative Deployment Options

### Netlify

Another excellent option with similar features:

1. Connect your GitHub repository
2. Build settings:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
3. Deploy

### GitHub Pages

For simple deployments:

1. Install gh-pages: `npm install --save-dev gh-pages`
2. Add to package.json:
   ```json
   {
     "scripts": {
       "deploy": "gh-pages -d dist"
     }
   }
   ```
3. Run: `npm run build && npm run deploy`

### Self-Hosted

For full control:

1. Build your app: `npm run build`
2. Upload `dist` folder to your web server
3. Configure your web server to serve the files
4. Ensure proper HTTPS setup

## 🔒 Security Considerations

### SSL Certificate

- ✅ **Vercel**: Automatic SSL included
- ✅ **Netlify**: Automatic SSL included
- ⚠️ **Self-hosted**: Configure SSL manually

### Environment Variables

Never commit sensitive data to your repository:

```bash
# Add to .gitignore
.env
.env.local
.env.production
```

### CORS Configuration

If you encounter CORS issues:

1. Use dedicated IPFS gateways
2. Configure proper headers in `vercel.json`
3. Consider using a proxy for external APIs

## 📊 Performance Optimization

### Build Optimization

Your `vite.config.js` is already optimized, but you can add:

```javascript
export default defineConfig({
  build: {
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ['@hashgraph/hedera-wallet-connect', '@hashgraph/sdk'],
          konva: ['konva']
        }
      }
    }
  }
});
```

### Asset Optimization

- 🖼️ **Images**: Use WebP format when possible
- 📦 **Bundles**: Code splitting is already configured
- 🗜️ **Compression**: Vercel handles this automatically

## 📈 Monitoring & Analytics

### Vercel Analytics

Enable in your Vercel dashboard for:
- Page views and performance metrics
- User engagement data
- Core Web Vitals monitoring

### Error Tracking

Consider adding error tracking:

```javascript
// Add to your main.js
window.addEventListener('error', (event) => {
  console.error('Application error:', event.error);
  // Send to your error tracking service
});
```

## 🔄 Continuous Deployment

### Automated Workflow

With Vercel + GitHub:

1. **Development**: Work on feature branches
2. **Preview**: Automatic preview deployments for PRs
3. **Production**: Merge to main triggers production deployment
4. **Rollback**: Easy rollback through Vercel dashboard

### Environment Strategy

- **Development**: Local development server
- **Preview**: Vercel preview deployments
- **Production**: Main branch deployment

## 🧪 Testing Your Deployment

### Pre-Deployment Checklist

- [ ] WalletConnect Project ID configured
- [ ] App metadata updated
- [ ] Assets uploaded and paths correct
- [ ] Build completes without errors
- [ ] Mobile responsiveness tested
- [ ] Wallet connection tested

### Post-Deployment Testing

1. **Functionality**: Test all features work
2. **Performance**: Check loading times
3. **Mobile**: Test on actual mobile devices
4. **Wallets**: Test with different Hedera wallets
5. **Networks**: Test from different locations

## 🆘 Troubleshooting

### Common Deployment Issues

**Build Fails**
- Check Node.js version compatibility
- Verify all dependencies are installed
- Review build logs for specific errors

**Assets Not Loading**
- Verify file paths are correct
- Check case sensitivity (important on Linux servers)
- Ensure files exist in the repository

**Wallet Connection Issues**
- Verify WalletConnect Project ID is correct
- Check HTTPS is enabled (required for wallet connections)
- Test with different wallets

### Getting Help

- 📖 Check Vercel documentation
- 💬 Join our Discord community
- 🐛 Report deployment issues on GitHub

## 🎉 Going Live

Once deployed:

1. 🧪 **Test thoroughly** with real users
2. 📢 **Announce** to your community
3. 📊 **Monitor** performance and usage
4. 🔄 **Iterate** based on feedback

---

*Ready to launch? Your Hedera NFT Overlay Tool is just a deploy away!*
