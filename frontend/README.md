# Frontend Build Guide

## Development

```bash
cd frontend
npm install
npm start
```

The frontend will run on `http://localhost:3001`

## Building for Production

```bash
npm run build
```

This creates an optimized production build in the `build` folder.

## Testing

```bash
npm test
```

## Project Structure

```
frontend/
├── public/           # Static files
├── src/
│  ├── components/    # Reusable components
│  ├── pages/        # Page components
│  ├── services/     # API services
│  ├── styles/       # CSS styles
│  ├── App.tsx       # Main app component
│  └── index.tsx     # Entry point
└── package.json
```

## Environment Variables

Create `.env.local`:

```env
REACT_APP_API_URL=http://localhost:3000/api
```

## Deployment

### Vercel
```bash
npm run build
vercel --prod
```

### Netlify
```bash
npm run build
netlify deploy --prod --dir=build
```

### Docker
See root `Dockerfile` for containerized deployment.
