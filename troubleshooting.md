# Actividad 4: Troubleshooting - Correcciones

## Snippet 1 - Corrección
### Error Original:
```yaml
name: CI Pipeline
on:
push
branches: [main]
pull_request
branches [main, develop]
jobs:
test:
runs-on: ubuntu-latest

### Error Corregido:
name: CI Pipeline
on:
  push:
    branches: [main]
  pull_request:
    branches: [main, develop]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4


### Snippet 2 - Corrección
### Error Original:
deploy:
  runs-on: ubuntu-latest
  environment: production
  steps:
  - uses: actions/checkout@v4
  - name: Deploy to Vercel
  run: vercel --prod --token $VERCEL_TOKEN
  env:
    VERCEL_TOKEN: secrets.VERCEL_TOKEN

###Error Corregido:
deploy:
  runs-on: ubuntu-latest
  environment: production
  steps:
    - uses: actions/checkout@v4
    - name: Deploy to Vercel
      run: vercel --prod --token $VERCEL_TOKEN
      env:
        VERCEL_TOKEN: ${{ secrets.VERCEL_TOKEN }}


### Snippet 3 - Corrección
### Error Original:
test:
  runs-on: ubuntu-latest
  strategy:
    matrix:
      node-version: 18
  steps:
  - uses: actions/checkout@v4
  - uses: actions/setup-node@v4
  with:
    node-version: ${matrix.node-version }}
    cache: npm
  - run: npm ci && npm test

###Error Corregido:
test:
  runs-on: ubuntu-latest
  strategy:
    matrix:
      node-version: [18.x, 20.x]
  steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci
    - run: npm test