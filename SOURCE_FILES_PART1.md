# Source Code - Redux Store & Utilities

## File: store/index.ts

```typescript
import { configureStore } from '@reduxjs/toolkit';
import cartReducer from './slices/cartSlice';
import wishlistReducer from './slices/wishlistSlice';

export const store = configureStore({
  reducer: {
    cart: cartReducer,
    wishlist: wishlistReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

## File: store/slices/cartSlice.ts

```typescript
import { createSlice, PayloadAction } from '@reduxjs/toolkit';

export interface CartItem {
  id: number;
  title: string;
  price: number;
  image: string;
  quantity: number;
}

interface CartState {
  items: CartItem[];
}

const initialState: CartState = { items: [] };

const cartSlice = createSlice({
  name: 'cart',
  initialState,
  reducers: {
    addToCart: (state, action: PayloadAction<Omit<CartItem, 'quantity'>>) => {
      const existing = state.items.find(i => i.id === action.payload.id);
      if (existing) {
        existing.quantity += 1;
      } else {
        state.items.push({ ...action.payload, quantity: 1 });
      }
    },
    updateQuantity: (
      state,
      action: PayloadAction<{ id: number; quantity: number }>
    ) => {
      const item = state.items.find(i => i.id === action.payload.id);
      if (item) item.quantity = action.payload.quantity;
    },
    removeFromCart: (state, action: PayloadAction<number>) => {
      state.items = state.items.filter(i => i.id !== action.payload);
    },
    clearCart: (state) => {
      state.items = [];
    },
  },
});

export const { addToCart, updateQuantity, removeFromCart, clearCart } = cartSlice.actions;
export default cartSlice.reducer;
```

## File: store/slices/wishlistSlice.ts

```typescript
import { createSlice, PayloadAction } from '@reduxjs/toolkit';

interface WishlistState {
  ids: number[];
}

const initialState: WishlistState = { ids: [] };

const wishlistSlice = createSlice({
  name: 'wishlist',
  initialState,
  reducers: {
    toggleWishlist: (state, action: PayloadAction<number>) => {
      const id = action.payload;
      if (state.ids.includes(id)) {
        state.ids = state.ids.filter(x => x !== id);
      } else {
        state.ids.push(id);
      }
    },
    clearWishlist: (state) => {
      state.ids = [];
    },
  },
});

export const { toggleWishlist, clearWishlist } = wishlistSlice.actions;
export default wishlistSlice.reducer;
```

## File: lib/searchInspector.ts

```typescript
export interface DebounceStatus {
  lastSearchTerm: string;
  searchCount: number;
}

let status: DebounceStatus = { lastSearchTerm: '', searchCount: 0 };
let lastToast = '';

export function recordSearch(term: string) {
  status.lastSearchTerm = term;
  status.searchCount += 1;
}

export function setLastToastMessage(msg: string) {
  lastToast = msg;
}

export function getLastToastMessage() {
  return lastToast;
}

export const debounceStatus = status;
```

## File: hooks/useDebounce.ts

```typescript
import { useEffect, useState } from 'react';
import { recordSearch } from '../lib/searchInspector';

export function useDebounce(value: string, delay: number = 300) {
  const [debounced, setDebounced] = useState(value);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebounced(value);
      if (value.trim()) {
        recordSearch(value.trim());
      }
    }, delay);

    return () => clearTimeout(handler);
  }, [value, delay]);

  return debounced;
}
```

## File: styles/globals.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  margin: 0;
  padding: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto',
    'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans',
    'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}

* {
  box-sizing: border-box;
}

/* Toast customization */
.Toastify__toast--success {
  @apply bg-green-600;
}

.Toastify__toast--error {
  @apply bg-red-600;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Remove default button styles */
button {
  font-family: inherit;
}
```

See SOURCE_FILES_PART2.md for Page Components
