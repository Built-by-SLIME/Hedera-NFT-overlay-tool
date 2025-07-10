# 🛠️ Setup Guide

This guide will walk you through setting up the Hedera NFT Overlay Tool from start to finish.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js)
- **Git** - [Download here](https://git-scm.com/)
- **Code Editor** (VS Code recommended)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Built-by-SLIME/Hedera-NFT-overlay-tool.git
cd Hedera-NFT-overlay-tool
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Start Development Server

```bash
npm run dev
```

Your app will be available at `http://localhost:5173`

## ⚙️ Configuration

### Required Configuration

#### 1. WalletConnect Project ID

1. Visit [WalletConnect Cloud](https://cloud.walletconnect.com/)
2. Create a new project
3. Copy your Project ID
4. Update `src/main.js` line 236:

```javascript
const projectId = 'YOUR_WALLETCONNECT_PROJECT_ID'; // Replace with your actual Project ID
```

#### 2. App Metadata

Update your app information in `src/main.js` lines 238-242:

```javascript
const metadata = {
  name: 'YOUR_APP_NAME',                    // Your app name
  description: 'NFT Overlay Tool for Hedera',
  url: 'https://your-domain.com',           // Your domain
  icons: ['/assets/icon/your_app_icon.png'], // Your app icon
};
```

### Optional Configuration

#### IPFS Gateways (Recommended)

For better performance, replace public gateways with your dedicated ones in `src/main.js` lines 13-18:

```javascript
const IPFS_GATEWAYS = [
  'https://your-dedicated-gateway.com/ipfs/',  // Your dedicated gateway
  'https://gateway.pinata.cloud/ipfs/',        // Fallback
  'https://gateway.lighthouse.storage/ipfs/'   // Fallback
];
```

**Recommended IPFS Providers:**
- [Pinata](https://pinata.cloud/) - Easy setup, generous free tier
- [Lighthouse](https://lighthouse.storage/) - Hedera-friendly
- [Infura](https://infura.io/) - Enterprise-grade

#### Single Token ID Mode

To limit the app to a specific NFT collection, modify the `fetchNFTs` function in `src/main.js` line 929:

```javascript
// Current (all NFTs):
let url = `https://mainnet.mirrornode.hedera.com/api/v1/accounts/${accountId}/nfts?limit=50`;

// Single token mode:
const targetTokenId = '0.0.YOUR_TOKEN_ID'; // Your specific token ID
let url = `https://mainnet.mirrornode.hedera.com/api/v1/accounts/${accountId}/nfts?token.id=${targetTokenId}&limit=50`;
```

## 🎨 Adding Assets

### Overlay Images

1. Add your overlay images to `public/assets/arts/`
2. Supported formats: PNG, JPG, SVG
3. Recommended: PNG with transparency for best results

### Fonts

1. Add custom fonts to `public/assets/fonts/`
2. Update CSS in `src/css/style.css` to reference your fonts

### Icons

1. Add app icons to `public/assets/icon/`
2. Update references in `index.html` and `src/main.js`

## 🔧 Environment Variables (Optional)

Create a `.env` file in the root directory:

```env
VITE_WALLETCONNECT_PROJECT_ID=your_project_id_here
VITE_APP_NAME=Your App Name
VITE_APP_URL=https://your-domain.com
VITE_TARGET_TOKEN_ID=0.0.123456  # Optional: for single token mode
```

Then update your code to use these variables:

```javascript
const projectId = import.meta.env.VITE_WALLETCONNECT_PROJECT_ID || 'YOUR_WALLETCONNECT_PROJECT_ID';
```

## 🧪 Testing

### Local Testing

```bash
npm run dev
```

### Network Testing (Mobile)

To test on mobile devices:

```bash
npm run dev -- --host
```

This will show network URLs you can access from mobile devices on the same WiFi.

### Build Testing

```bash
npm run build
npm run preview
```

## 🔍 Troubleshooting

### Common Issues

**Issue**: WalletConnect not working
- **Solution**: Verify your Project ID is correct and active

**Issue**: NFTs not loading
- **Solution**: Check browser console for CORS errors, may need dedicated IPFS gateway

**Issue**: Images not displaying
- **Solution**: Ensure image paths are correct and files exist in `public/assets/`

**Issue**: Mobile touch not working
- **Solution**: Verify `touch-action: none` is set in CSS

### Getting Help

- 📖 Check our [Deployment Guide](DEPLOYMENT.md)
- 💬 Join our Discord community
- 🐛 Report issues on GitHub

## 🎯 Next Steps

Once setup is complete:

1. 📖 Read the [Deployment Guide](DEPLOYMENT.md) to go live
2. 🎨 Customize the UI to match your brand
3. 📱 Test thoroughly on mobile devices
4. 🚀 Deploy and share with your community!

---

*Need help? The SLIME community is here to support you!*
