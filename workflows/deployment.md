---
description: Workflow for deploying applications end-to-end
---

# Deployment Workflow

Steps for building, testing, staging, and deploying applications.

## Steps

### 1. Pre-Deployment Checklist
- [ ] All tests pass on the deployment branch
- [ ] Code review is approved and merged
- [ ] Database migrations are reviewed and tested
- [ ] Environment variables are configured
- [ ] No known critical bugs

### 2. Build
```bash
# Build the production bundle
npm run build          # Node.js/Frontend
docker build -t app .  # Docker
```

- Verify the build succeeds without warnings
- Check bundle size is within acceptable limits

### 3. Run Tests Against Build
```bash
# Final test pass against the production build
npm run test:ci
```

### 4. Deploy to Staging
- Deploy the build to the staging environment
- Verify staging configuration matches production
- Run smoke tests on staging

### 5. Staging Verification
- Verify critical user flows work
- Check logs for errors
- Verify database migrations applied correctly
- Performance spot-check

### 6. Deploy to Production
- Deploy using the same artifact tested in staging
- Apply database migrations first (if any)
- Use rolling deployment to minimize downtime
- Monitor logs and metrics during rollout

### 7. Post-Deployment Verification
- Run smoke tests on production
- Monitor error rates and response times
- Verify key metrics haven't degraded
- Check external integrations are working

### 8. Rollback Plan
If issues are detected:
1. Revert to the previous deployment
2. Rollback database migrations (if applicable)
3. Notify the team
4. Create an incident report
5. Fix forward with a hotfix if rollback isn't possible
