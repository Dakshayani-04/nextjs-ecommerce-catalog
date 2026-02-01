# Quick Start Guide - Next.js E-Commerce Catalog

## 🚀 Get Running in 5 Minutes

### Option 1: Local Development (Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/Dakshayani-04/nextjs-ecommerce-catalog.git
cd nextjs-ecommerce-catalog

# 2. Install dependencies
npm install

# 3. Copy environment variables
cp .env.example .env.local

# 4. Run development server
npm run dev

# 5. Open http://localhost:3000 in your browser
```

### Option 2: Docker

```bash
# Clone and navigate
git clone https://github.com/Dakshayani-04/nextjs-ecommerce-catalog.git
cd nextjs-ecommerce-catalog

# Build and run
docker-compose up --build

# Open http://localhost:3000 in your browser

# Check health
curl http://localhost:3000/api/health
```

## 📖 What to Try First

1. **Homepage** → `http://localhost:3000`
   - Welcome page with feature overview

2. **Products Listing** → `http://localhost:3000/products`
   - Browse products with pagination
   - Try search: type "computer"
   - Try filtering: click category buttons

3. **Product Details** → Click any product
   - View full details
   - Add to cart → notification appears
   - Add to wishlist → heart icon updates

4. **Shopping Cart** → `http://localhost:3000/cart`
   - View items
   - Update quantities
   - Remove items

## 🧪 Test with Window Functions

Open browser console (F12) and test:

```javascript
// Check cart contents
window.getCartState()

// Check wishlist
window.getWishlistState()

// Check search tracking
window.getDebounceStatus()

// Check last toast
window.getLastToastMessage()
```

## 📚 Documentation

- **[README.md](./README.md)** - Full project documentation
- **[IMPLEMENTATION_GUIDE.md](./IMPLEMENTATION_GUIDE.md)** - Detailed setup
- **[SOURCE_FILES_PART1.md](./SOURCE_FILES_PART1.md)** - Code reference

## 🛠️ Available Commands

```bash
npm run dev      # Development server
npm run build    # Production build
npm run start    # Run production build
npm run lint     # ESLint check
```

## 🐳 Docker Commands

```bash
# Build only
docker build -t nextjs-ecommerce .

# Run specific container
docker run -p 3000:3000 nextjs-ecommerce

# Docker Compose
docker-compose up          # Run
docker-compose down        # Stop
docker-compose logs -f     # View logs
```

## ⚙️ Configuration

Edit `.env.local`:

```env
NEXT_PUBLIC_API_URL=https://fakestoreapi.com  # API endpoint
PORT=3000                                       # Server port
NODE_ENV=development                            # Environment
```

## 🎯 Next Steps

1. Review the [README.md](./README.md) for full feature list
2. Check [IMPLEMENTATION_GUIDE.md](./IMPLEMENTATION_GUIDE.md) for architecture
3. Explore [SOURCE_FILES_PART1.md](./SOURCE_FILES_PART1.md) for code patterns
4. Test all features in the UI
5. Use window functions for automated testing

## 🆘 Troubleshooting

**Port 3000 already in use?**
```bash
# Use different port
PORT=3001 npm run dev
```

**API errors?**
```bash
# Check FakeStoreAPI is accessible
curl https://fakestoreapi.com/products
```

**Docker issues?**
```bash
# Rebuild images
docker-compose down
docker-compose up --build
```

## ✅ Project Status

✅ All core features implemented
✅ Docker containerization ready
✅ Comprehensive documentation provided
✅ 10+ commits pushed to GitHub
✅ Ready for production deployment

---

**Need help?** Check the full README or IMPLEMENTATION_GUIDE for detailed information.
