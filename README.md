# 🛍️ Next.js E-Commerce Product Catalog

A modern, feature-rich e-commerce product catalog built with **Next.js 14**, **Redux Toolkit**, **Tailwind CSS**, and integrated with the **FakeStoreAPI**. This project demonstrates best practices for server-side rendering, state management, and building scalable e-commerce applications.

## ✨ Key Features

- ✅ **Server-Side Rendering (SSR)** - Fast initial page loads and excellent SEO
- ✅ **Redux Toolkit** - Centralized state management for cart and wishlist
- ✅ **Advanced Product Filtering** - Filter by category with URL parameters
- ✅ **Debounced Search** - Optimized search with 300ms debounce
- ✅ **Pagination** - Server-side pagination (10 items per page)
- ✅ **Shopping Cart** - Add, update quantity, and remove items
- ✅ **Wishlist** - Toggle products to wishlist
- ✅ **Toast Notifications** - User feedback for actions
- ✅ **Dynamic SEO** - Meta tags optimized for each product
- ✅ **Docker** - Ready for containerization
- ✅ **TypeScript** - Full type safety
- ✅ **Tailwind CSS** - Beautiful, responsive design
- ✅ **FakeStoreAPI** - Real product data

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- npm or yarn
- Docker & Docker Compose (optional)

### Local Development

```bash
# Clone the repository
git clone https://github.com/Dakshayani-04/nextjs-ecommerce-catalog.git
cd nextjs-ecommerce-catalog

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local

# Run development server
npm run dev

# Open http://localhost:3000 in your browser
```

### Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Access at http://localhost:3000

# Check health
curl http://localhost:3000/api/health
```

## 📁 Project Structure

```
nextjs-ecommerce-catalog/
├── pages/
│   ├── api/
│   │   └── health.ts          # Health check endpoint
│   ├── products/
│   │   ├── index.tsx          # Products listing with SSR & pagination
│   │   └── [id].tsx           # Product detail page with SEO
│   ├── _app.tsx               # App wrapper with Redux Provider
│   ├── index.tsx              # Homepage
│   └── cart.tsx               # Shopping cart page
├── components/
│   └── layout/
│       └── Layout.tsx         # Shared layout with header/footer
├── store/
│   ├── index.ts               # Redux store configuration
│   └── slices/
│       ├── cartSlice.ts       # Cart reducer logic
│       └── wishlistSlice.ts   # Wishlist reducer logic
├── hooks/
│   └── useDebounce.ts         # Debounce hook for search
├── lib/
│   └── searchInspector.ts     # Search state tracking for testing
├── styles/
│   └── globals.css            # Global Tailwind CSS
├── Dockerfile                 # Docker configuration
├── docker-compose.yml         # Docker Compose setup
├── .env.example               # Environment variables template
├── package.json               # Dependencies
├── tsconfig.json              # TypeScript configuration
└── README.md                  # This file
```

## 📚 Documentation

- **[IMPLEMENTATION_GUIDE.md](./IMPLEMENTATION_GUIDE.md)** - Detailed setup and implementation instructions
- **[SOURCE_FILES_PART1.md](./SOURCE_FILES_PART1.md)** - Redux store, utilities, and styles code

## 🔧 Configuration

### Environment Variables

Create `.env.local` from `.env.example`:

```env
NEXT_PUBLIC_API_URL=https://fakestoreapi.com
PORT=3000
NODE_ENV=development
```

## 🎯 Core Features

### 1. Server-Side Rendering
- Products page fetches data on server using `getServerSideProps`
- Initial HTML contains rendered product list
- Excellent SEO and fast perceived performance

### 2. Pagination
- 10 products per page
- Server-side pagination with `limit` and `offset`
- Previous/Next navigation buttons
- Query parameters for shareability

### 3. Filtering
- Filter by category (electronics, jewelery, men's clothing, women's clothing)
- URL-based filters for bookmarkability
- Real-time product list updates

### 4. Debounced Search
- Optimized with 300ms debounce
- Prevents excessive re-renders
- Search tracking exposed for testing

### 5. Shopping Cart
- Redux-based state management
- Add items with quantity tracking
- Update quantities
- Remove items
- Window function for testing: `window.getCartState()`

### 6. Wishlist
- Toggle items on/off
- Redux-based storage
- Window function for testing: `window.getWishlistState()`

### 7. Toast Notifications
- User-friendly feedback for cart actions
- Window function for testing: `window.getLastToastMessage()`

### 8. SEO Meta Tags
- Dynamic title and description
- Product-specific metadata
- Optimized for search engines

## 🧪 Testing Features

In development mode, test the application with window functions:

```javascript
// Get current cart state
window.getCartState()  
// Returns: { items: [...] }

// Get current wishlist state
window.getWishlistState()  
// Returns: { ids: [...] }

// Get debounce tracking
window.getDebounceStatus()  
// Returns: { lastSearchTerm: "...", searchCount: N }

// Get last toast message
window.getLastToastMessage()  
// Returns: "Item added to cart!"
```

## 🐳 Docker

### Build
```bash
docker build -t nextjs-ecommerce .
```

### Run
```bash
docker run -p 3000:3000 nextjs-ecommerce
```

### Docker Compose
```bash
docker-compose up
```

## 📊 API Integration

All data comes from **FakeStoreAPI**:
- **Products**: `https://fakestoreapi.com/products`
- **Single Product**: `https://fakestoreapi.com/products/{id}`
- **Categories**: `https://fakestoreapi.com/products/categories`

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Next.js 14** | React framework with SSR support |
| **React 18** | UI library |
| **Redux Toolkit** | State management |
| **TypeScript** | Type safety |
| **Tailwind CSS** | Styling |
| **Axios** | HTTP requests |
| **React Toastify** | Notifications |
| **Docker** | Containerization |

## 📖 Usage Examples

### Browse Products
1. Visit `http://localhost:3000/products`
2. View first 10 products
3. Navigate with pagination

### Search Products
1. Use search input on products page
2. Type slowly or fast - debounce handles it
3. Products filter in real-time

### Filter by Category
1. Click category buttons
2. Page updates to show filtered products
3. URL updates with query parameter

### Add to Cart
1. Click product to view details
2. Click "Add to Cart"
3. Toast notification appears
4. Cart count updates in header

### View Cart
1. Click "Cart" in header
2. See all items with quantities
3. Update quantities or remove items

### Manage Wishlist
1. Click heart icon on product details
2. Add/remove from wishlist
3. Wishlist count updates in header

## 🚀 Performance Optimizations

- **SSR**: Server-side rendering for fast initial load
- **Code Splitting**: Automatic with Next.js
- **Image Optimization**: Next.js Image component (can be added)
- **Debounced Search**: Reduces API calls and re-renders
- **Redux Selectors**: Memoized state selection
- **CSS-in-JS**: Tailwind for optimized styles

## 🔐 Security

- Type-safe with TypeScript
- No sensitive data in client-side code
- Environment variables for configuration
- HTTPS ready (NEXT_PUBLIC_API_URL)

## 📝 License

MIT License - Feel free to use this project for learning and development.

## 👤 Author

**Dakshayani-04**
- GitHub: [@Dakshayani-04](https://github.com/Dakshayani-04)

## 🤝 Contributing

Contributions are welcome! Feel free to open issues and pull requests.

## 📞 Support

For issues or questions, please open an issue on GitHub.

---

**Built with ❤️ using Next.js, Redux Toolkit, and Tailwind CSS**
