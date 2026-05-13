# Digital Products Store - Specification Document

## 1. Project Overview

**Project Name:** DigitStore
**Project Type:** E-commerce Web Application
**Core Functionality:** A fully functional digital products marketplace with customer-facing store and admin panel for product management, integrated with Dodo Payments for processing payments.
**Target Users:** Digital product creators (sellers) and customers (buyers)

---

## 2. Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **Payments:** Dodo Payments SDK
- **Data Storage:** LocalStorage (client-side) + API routes for server-side operations
- **Deployment:** Netlify

---

## 3. UI/UX Specification

### 3.1 Design Theme
- **Style:** Modern, dark-themed e-commerce with neon accents
- **Aesthetic:** Cyberpunk/tech-inspired with premium feel

### 3.2 Color Palette
```css
--bg-primary: #0a0a0f (Deep black)
--bg-secondary: #12121a (Dark navy)
--bg-card: #1a1a24 (Card background)
--accent-primary: #00ff88 (Neon green)
--accent-secondary: #ff00aa (Neon pink)
--accent-tertiary: #00d4ff (Neon cyan)
--text-primary: #ffffff
--text-secondary: #a0a0b0
--text-muted: #6b6b7b
--border-color: #2a2a3a
--success: #00ff88
--error: #ff4466
```

### 3.3 Typography
- **Headings:** "Orbitron" (Google Font) - futuristic, bold
- **Body:** "Inter" (Google Font) - clean, readable
- **Sizes:**
  - H1: 48px / 3rem
  - H2: 36px / 2.25rem
  - H3: 24px / 1.5rem
  - Body: 16px / 1rem
  - Small: 14px / 0.875rem

### 3.4 Spacing System
- Base unit: 4px
- Spacing scale: 4, 8, 12, 16, 24, 32, 48, 64, 96px

### 3.5 Layout Structure

#### Customer Store Pages
- **Header:** Fixed navigation with logo, nav links, cart icon with badge
- **Hero:** Full-width banner with featured product/CTA
- **Product Grid:** 3 columns on desktop, 2 on tablet, 1 on mobile
- **Footer:** Site links, contact, social icons

#### Admin Pages
- **Sidebar:** Fixed left sidebar with navigation
- **Main Content:** Header + content area
- **Responsive:** Collapsible sidebar on mobile

### 3.6 Responsive Breakpoints
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

### 3.7 Visual Effects
- Neon glow effects on buttons and accents
- Subtle gradient backgrounds
- Card hover: scale(1.02) + glow
- Page transitions: fade-in
- Loading states: skeleton loaders

---

## 4. Page Specifications

### 4.1 Customer Pages

#### Home Page (`/`)
- Hero section with animated gradient background
- Featured products carousel
- Product categories showcase
- Newsletter signup
- Trust badges

#### Products Page (`/products`)
- Filter sidebar (categories, price range)
- Search bar
- Product grid with pagination
- Sort options (price, name, newest)

#### Product Detail Page (`/products/[id]`)
- Product images gallery
- Title, description, price
- "Add to Cart" button
- Product specifications
- Related products

#### Cart Page (`/cart`)
- Cart items list with quantities
- Update quantity controls
- Remove item button
- Subtotal calculation
- Proceed to checkout button

#### Checkout Page (`/checkout`)
- Order summary
- Customer information form
- Payment integration (Dodo Payments)
- Order confirmation

### 4.2 Admin Pages

#### Admin Dashboard (`/admin`)
- Stats overview (total products, orders, revenue)
- Recent orders list
- Quick actions
- Sales chart (last 7 days)

#### Products Management (`/admin/products`)
- Products table with search
- Add new product button
- Edit/Delete actions
- Bulk actions

#### Add/Edit Product (`/admin/products/new`, `/admin/products/[id]/edit`)
- Product name input
- Description textarea
- Price input
- Category dropdown
- Image URL input
- File upload for digital product
- Active/Inactive toggle

#### Orders Management (`/admin/orders`)
- Orders table with status
- Order details modal
- Update order status

---

## 5. Functionality Specification

### 5.1 Product Management (Admin)
- Create new product with: name, description, price, category, image, digital file
- Edit existing products
- Delete products (with confirmation)
- View all products in table format
- Search and filter products

### 5.2 Shopping Cart (Customer)
- Add products to cart
- Update quantities
- Remove items
- Persist cart in localStorage
- Show cart count in header

### 5.3 Checkout & Payments (Customer)
- Customer information collection
- Dodo Payments integration for payment processing
- Order creation on successful payment
- Order confirmation page
- Email confirmation (optional)

### 5.4 Data Management
- Products stored in localStorage (simulated database)
- Orders stored in localStorage
- Admin authentication (simple password protection)

---

## 6. Dodo Payments Integration

### Configuration
- Use Dodo Payments SDK
- Environment: Sandbox mode for testing
- Payment methods: Card payments

### Checkout Flow
1. Customer reviews cart
2. Click "Checkout"
3. Enter customer details
4. Redirect to Dodo Payments checkout
5. Process payment
6. Return to success/cancel page

---

## 7. Component Specifications

### Navigation Component
- Logo (left)
- Nav links: Home, Products (center)
- Cart icon with badge (right)
- Mobile: hamburger menu

### Product Card Component
- Image container (aspect-ratio: 1)
- Product name
- Price
- Category badge
- "Add to Cart" button
- Hover: glow effect + scale

### Product Form Component (Admin)
- All form fields with validation
- Image preview
- File upload dropzone
- Save/Cancel buttons

### Cart Item Component
- Product thumbnail
- Product name
- Unit price
- Quantity selector
- Remove button
- Line total

---

## 8. Sample Data

### Default Products
1. **Premium UI Kit** - $49.99 - Category: UI Kits
2. **Icon Pack Pro** - $29.99 - Category: Icons
3. **eBook: Web Dev Mastery** - $19.99 - Category: eBooks
4. **Code Snippets Bundle** - $39.99 - Category: Code
5. **Video Course: React** - $79.99 - Category: Courses

---

## 9. Acceptance Criteria

### Store Functionality
- [ ] Homepage loads with hero and featured products
- [ ] Products page displays all products with filters
- [ ] Product detail page shows full information
- [ ] Add to cart works and persists
- [ ] Cart page shows all items with totals
- [ ] Checkout collects customer info
- [ ] Dodo Payments processes payments
- [ ] Order confirmation displays after payment

### Admin Functionality
- [ ] Admin login with password
- [ ] Dashboard shows stats
- [ ] Can add new products
- [ ] Can edit existing products
- [ ] Can delete products
- [ ] Products table displays correctly

### Technical
- [ ] Builds without errors
- [ ] Responsive on all breakpoints
- [ ] No console errors
- [ ] Netlify deployment ready
- [ ] Payment integration functional

---

## 10. File Structure

```
/app
  /page.tsx (homepage)
  /products/page.tsx
  /products/[id]/page.tsx
  /cart/page.tsx
  /checkout/page.tsx
  /admin/page.tsx (dashboard)
  /admin/products/page.tsx
  /admin/products/new/page.tsx
  /admin/products/[id]/edit/page.tsx
  /admin/orders/page.tsx
  /api/products/route.ts
  /api/orders/route.ts
  /api/payments/route.ts
/components
  /layout/Header.tsx
  /layout/Footer.tsx
  /layout/AdminSidebar.tsx
  /ui/Button.tsx
  /ui/Input.tsx
  /ui/Modal.tsx
  /ui/ProductCard.tsx
  /ui/CartItem.tsx
  ...
/lib
  /dodo.ts
  /storage.ts
  /types.ts
/public
  /images
```