# Fashion Shop - Midtrans Payment Integration

A simple product checkout application built with Next.js 13 (App Router) and Tailwind CSS to demonstrate integrating Midtrans as a payment gateway in a sandbox environment.

This repository covers two common payment flows offered by Midtrans:
- **Snap Checkout Popup**: Generates a transaction token on the server and opens the Midtrans Snap payment modal directly on the page.
- **Payment Link API**: Requests a standalone Midtrans payment URL via Basic Authentication.

## Tech Stack

- **Framework**: Next.js 13 (App Router)
- **Styling**: Tailwind CSS
- **Payment Gateway**: Midtrans (`midtrans-client` & REST API)

## Getting Started

### 1. Clone and Install Dependencies

```bash
git clone https://github.com/muzaim/fashion-shop-midtrans.git
cd fashion-shop-midtrans
npm install
```

### 2. Configure Environment Variables

Create a `.env` file in the project root and add your Midtrans Sandbox credentials (available in your Midtrans Dashboard under **Settings > Access Keys**):

```env
NEXT_PUBLIC_CLIENT=SB-Mid-client-xxxxxxxxxxxxxxxx
NEXT_PUBLIC_SECRET=SB-Mid-server-xxxxxxxxxxxxxxxx
NEXT_PUBLIC_API=https://api.sandbox.midtrans.com
```

### 3. Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to test the checkout flow.

## Project Structure

- `app/page.js` — Main product page and Midtrans `snap.js` script loader.
- `app/components/Checkout.jsx` — Quantity selector, Snap popup trigger, and Payment Link generator.
- `app/api/tokenizer/route.js` — API route that initializes `midtrans-client` and returns a Snap transaction token.
- `app/libs/product.js` — Mock product data used for checkout calculations.
- `app/thanks/page.js` — Post-payment confirmation page.

## Notes

This project is intended for learning and sandbox testing. Before moving a similar implementation to production, ensure that your Midtrans Server Key is kept strictly on the server side (without the `NEXT_PUBLIC_` prefix) and that product prices are validated on the backend rather than trusted from client requests.
