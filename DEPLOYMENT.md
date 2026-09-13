# Deployment Guide

## Quick Start

### Local Development
```bash
npm install
npm run dev
```

### Docker Local
```bash
docker-compose up
```

## Production Deployment

### Prerequisites
- Node.js 18+
- PostgreSQL database
- Environment variables configured

### Environment Setup

1. Copy `.env.example` to `.env.local`:
```bash
cp .env.example .env.local
```

2. Update the environment variables with production values:
```env
DATABASE_URL=your_production_db_url
JWT_SECRET=your_production_jwt_secret
NODE_ENV=production
```

### Deployment Options

#### Option 1: Docker (Recommended)

Build and run:
```bash
docker build -t fantastic-octo-train .
docker run -p 3000:3000 \
  -e DATABASE_URL=your_db_url \
  -e JWT_SECRET=your_secret \
  fantastic-octo-train
```

#### Option 2: Manual Deployment

```bash
npm install --production
npm run build
npm start
```

#### Option 3: Docker Compose (with Database)

```bash
docker-compose up -d
```

### Cloud Platforms

#### AWS EC2
```bash
# After connecting to instance
git clone https://github.com/Neuroai12/fantastic-octo-train.git
cd fantastic-octo-train
npm install
npm run build
pm2 start dist/index.js --name "fantastic-octo"
```

#### Heroku
```bash
heroku create fantastic-octo-train
git push heroku main
```

#### Railway / Render / Vercel
- Connect your GitHub repository
- Set environment variables
- Deploy automatically on push

## Health Checks

The application includes a health check endpoint at `/health`.

Test it:
```bash
curl http://localhost:3000/health
```

## Monitoring

- Monitor logs: `docker logs container_id`
- Check application status: `npm run health`
- Database connection: Ensure `DATABASE_URL` is accessible

## Scaling

- Use load balancers for multiple instances
- Implement caching strategies
- Configure database connection pooling
- Monitor performance metrics

## Security Checklist

- [ ] JWT_SECRET is strong and unique
- [ ] DATABASE_URL uses SSL connection
- [ ] CORS_ORIGIN is restricted to your domain
- [ ] Environment variables are not in version control
- [ ] Rate limiting is enabled
- [ ] HTTPS is enforced in production
- [ ] Regular security updates are applied

## Rollback

If deployment fails:
```bash
docker rollback to previous-version
# or
git revert HEAD
npm run build
npm start
```

## Support

For deployment issues, check the logs and verify all environment variables are set correctly.
