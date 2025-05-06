# Simple-OS (Vuepabase)

A modern Vue 3 application with Supabase authentication integration, featuring email, password, and GitHub authentication flows. This project demonstrates how to effectively integrate Supabase with Vue 3, Pinia, Vue-router 4, TailwindCSS, and includes testing with Vitest and Cypress.

## Features

- 🔐 Complete authentication system with Supabase
- 📧 Email & Password authentication
- 🔑 GitHub OAuth integration
- 💱 KHQR payment integration
- 🧩 Vue 3 Composition API
- 🏪 Pinia for state management
- 🛣️ Vue Router for navigation
- 🎨 TailwindCSS for styling
- 🧪 Testing with Vitest and Cypress

## Prerequisites

- Node.js (v16 or later recommended)
- npm or yarn
- Git
- Supabase account

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/MyKhode/ihub.git
   cd ihub
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory based on the example below:
   ```
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

## Development Setup

### Supabase Configuration

1. Head over to [Supabase](https://supabase.com/) and create a new project
2. Choose your Project name, password, region, and pricing plan (free tier works fine)
3. Once the project is created, navigate to **Authentication > Settings**
4. Configure Site URL and Additional Redirect URLs:

   | Field                    | Value                                                                                                                                                                                              |
   |--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Site URL                 | `https://your-production-url.com/`                                                                                                                                                                 |
   | Additional Redirect URLs | `http://localhost:3000/resetpassword`, `https://your-production-url.com/resetpassword`, `http://localhost:3000`, `http://localhost:3000/callback`, `https://your-production-url.com/callback` |

5. Save your changes

### GitHub OAuth Setup (Optional)

1. Go to [GitHub Developer Settings](https://github.com/settings/developers)
2. Create a new OAuth App
3. Set the Authorization callback URL to your Supabase Auth callback URL (found in Supabase Dashboard)
4. Copy the Client ID and Client Secret
5. In Supabase Dashboard, go to **Authentication > Providers**
6. Enable GitHub provider and enter your Client ID and Client Secret
7. Save your changes

### KHQR Configuration

The KHQR (Khmer QR Code) payment integration requires specific setup:

1. Import the KHQR module in your component:
   ```javascript
   import { khqr } from 'ts-khqr';
   ```

2. Configure KHQR parameters in your application:
   ```javascript
   const qrData = khqr.generate({
     merchantName: 'YOUR_MERCHANT_NAME',
     merchantID: 'YOUR_MERCHANT_ID',
     merchantCity: 'YOUR_CITY',
     amount: transactionAmount,
     currency: 'USD', // or 'KHR' for Cambodian Riel
     acquiringBank: 'YOUR_ACQUIRING_BANK',
     billNumber: 'UNIQUE_BILL_ID'
   });
   ```

3. Generate a QR code using the qrcode library:
   ```javascript
   import QRCode from 'qrcode';
   
   // Generate QR code in component
   QRCode.toCanvas(document.getElementById('qr-canvas'), qrData, {
     width: 250,
     margin: 2
   });
   ```

4. Set up payment listener in your Pinia store or component to handle transaction callbacks.

## Running the Application

### Development Mode

```bash
npm run dev
```

This will start the development server at `http://localhost:3000`

### Build for Production

```bash
npm run build
```

### Preview Production Build

```bash
npm run preview
```

This will serve the production build at `http://localhost:5050`

## Testing

### Unit Tests with Vitest

```bash
npm run test:vitest
```

### Component Tests with Cypress

```bash
npm run test:unit
```

### E2E Tests with Cypress

```bash
npm run test:e2e
```

## API Endpoints

If you're using the integrated server functionality:

```bash
npm run serve
```

This will start the server defined in `server.js`

## Project Structure

```
├── public/               # Static assets
├── src/
│   ├── assets/           # App assets (processed by Vite)
│   ├── components/       # Vue components
│   ├── composables/      # Vue composables
│   ├── layouts/          # Page layouts
│   ├── router/           # Vue Router configuration
│   ├── stores/           # Pinia stores
│   ├── services/         # API services
│   │   └── supabase.ts   # Supabase client configuration
│   ├── types/            # TypeScript type definitions
│   ├── utils/            # Utility functions
│   ├── views/            # Page components
│   ├── App.vue           # Root component
│   └── main.ts           # Application entry point
├── .env                  # Environment variables
├── .env.example          # Example environment variables
├── cypress/              # Cypress test files
├── cypress.json          # Cypress configuration
├── vite.config.ts        # Vite configuration
├── tsconfig.json         # TypeScript configuration
└── tailwind.config.js    # Tailwind CSS configuration
```

## Deployment

1. Build your application for production
   ```bash
   npm run build
   ```

2. Deploy the contents of the `dist` folder to your web hosting service

3. Make sure to configure your hosting service to handle SPA routing by redirecting all requests to `index.html`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

ISC

## Links

- Repository: [https://github.com/MyKhode/ihub](https://github.com/MyKhode/ihub)
- Issues: [https://github.com/MyKhode/ihub/issues](https://github.com/MyKhode/ihub/issues)
- Supabase Documentation: [https://supabase.com/docs](https://supabase.com/docs)
- Vue 3 Documentation: [https://vuejs.org/guide/introduction.html](https://vuejs.org/guide/introduction.html)
- KHQR Documentation: [https://www.npmjs.com/package/ts-khqr](https://www.npmjs.com/package/ts-khqr)
