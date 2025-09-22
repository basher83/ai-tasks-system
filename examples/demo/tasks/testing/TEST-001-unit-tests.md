---
Task: Add Unit Test Framework
Task ID: TEST-001
Priority: P1 (Important)
Estimated Time: 3 hours
Dependencies: DEV-003
Status: ⏸️ Blocked
Created: 2025-01-22
Updated: 2025-01-22
---

## Objective

Set up a comprehensive unit testing framework with Jest and React Testing Library. This establishes the foundation for testing components, utilities, and business logic.

## Prerequisites

- [ ] Build system configured (DEV-003)
- [ ] Dependencies installed (DEV-002)
- [ ] Project structure in place

## Implementation Steps

### 1. **Install Testing Dependencies**

Add testing framework and utilities:

```bash
# Install Jest and React Testing Library
npm install --save-dev jest@29 jest-environment-jsdom@29
npm install --save-dev @testing-library/react@14 @testing-library/jest-dom@6
npm install --save-dev @testing-library/user-event@14

# Install additional testing utilities
npm install --save-dev msw@2
npm install --save-dev vitest@0.34 @vitest/ui@0.34
```

### 2. **Create Jest Configuration**

Set up Jest configuration:

```bash
# Create jest.config.js
cat > jest.config.js << 'EOF'
const nextJest = require('next/jest')

const createJestConfig = nextJest({
  // Provide the path to your Next.js app to load next.config.js and .env files
  dir: './',
})

// Add any custom config to be passed to Jest
const customJestConfig = {
  setupFilesAfterEnv: ['<rootDir>/jest.setup.js'],
  moduleNameMapping: {
    // Handle module aliases (this will be automatically configured for you based on your tsconfig.json paths)
    '^@/(.*)$': '<rootDir>/$1',
    '^@/components/(.*)$': '<rootDir>/src/components/$1',
    '^@/lib/(.*)$': '<rootDir>/src/lib/$1',
  },
  testEnvironment: 'jest-environment-jsdom',
  collectCoverageFrom: [
    'src/**/*.{js,jsx,ts,tsx}',
    '!src/**/*.d.ts',
    '!src/**/_*.{js,jsx,ts,tsx}',
  ],
  coverageThreshold: {
    global: {
      branches: 70,
      functions: 70,
      lines: 70,
      statements: 70,
    },
  },
}

// createJestConfig is exported this way to ensure that next/jest can load the Next.js config which is async
module.exports = createJestConfig(customJestConfig)
EOF
```

### 3. **Create Jest Setup File**

Configure test environment:

```bash
# Create jest.setup.js
cat > jest.setup.js << 'EOF'
import '@testing-library/jest-dom'

// Mock IntersectionObserver
global.IntersectionObserver = class IntersectionObserver {
  constructor() {}
  disconnect() {}
  observe() {}
  unobserve() {}
}

// Mock ResizeObserver
global.ResizeObserver = class ResizeObserver {
  constructor() {}
  disconnect() {}
  observe() {}
  unobserve() {}
}

// Mock matchMedia
Object.defineProperty(window, 'matchMedia', {
  writable: true,
  value: jest.fn().mockImplementation(query => ({
    matches: false,
    media: query,
    onchange: null,
    addListener: jest.fn(), // deprecated
    removeListener: jest.fn(), // deprecated
    addEventListener: jest.fn(),
    removeEventListener: jest.fn(),
    dispatchEvent: jest.fn(),
  })),
})
EOF
```

### 4. **Create Test Structure**

Set up test directories and initial tests:

```bash
# Create test utilities
mkdir -p tests/utils tests/mocks

# Create test utility file
cat > tests/utils/test-utils.tsx << 'EOF'
import React, { ReactElement } from 'react'
import { render, RenderOptions } from '@testing-library/react'
import { BrowserRouter } from 'react-router-dom'

const AllTheProviders = ({ children }: { children: React.ReactNode }) => {
  return <BrowserRouter>{children}</BrowserRouter>
}

const customRender = (
  ui: ReactElement,
  options?: Omit<RenderOptions, 'wrapper'>
) => render(ui, { wrapper: AllTheProviders, ...options })

export * from '@testing-library/react'
export { customRender as render }
EOF

# Create first component test
cat > src/components/auth/__tests__/LoginForm.test.tsx << 'EOF'
import { render, screen, fireEvent } from '@/tests/utils/test-utils'
import LoginForm from '../LoginForm'

describe('LoginForm', () => {
  it('renders login form correctly', () => {
    render(<LoginForm />)

    expect(screen.getByLabelText('Email')).toBeInTheDocument()
    expect(screen.getByLabelText('Password')).toBeInTheDocument()
    expect(screen.getByRole('button', { name: /sign in/i })).toBeInTheDocument()
  })

  it('allows user to type in email and password', () => {
    render(<LoginForm />)

    const emailInput = screen.getByLabelText('Email')
    const passwordInput = screen.getByLabelText('Password')

    fireEvent.change(emailInput, { target: { value: 'test@example.com' } })
    fireEvent.change(passwordInput, { target: { value: 'password123' } })

    expect(emailInput).toHaveValue('test@example.com')
    expect(passwordInput).toHaveValue('password123')
  })

  it('submits form when button is clicked', async () => {
    render(<LoginForm />)

    const emailInput = screen.getByLabelText('Email')
    const passwordInput = screen.getByLabelText('Password')
    const submitButton = screen.getByRole('button', { name: /sign in/i })

    fireEvent.change(emailInput, { target: { value: 'test@example.com' } })
    fireEvent.change(passwordInput, { target: { value: 'password123' } })
    fireEvent.click(submitButton)

    // Add assertions based on your authentication logic
    expect(submitButton).toBeDisabled()
  })
})
EOF
```

### 5. **Update Package.json Scripts**

Add test scripts:

```bash
# Update package.json with test scripts
npm pkg set scripts.test="jest"
npm pkg set scripts.test:watch="jest --watch"
npm pkg set scripts.test:coverage="jest --coverage"
npm pkg set scripts.test:ci="jest --ci --coverage --watchAll=false"
```

## Success Criteria

- [ ] Jest configuration created and working
- [ ] Test environment properly mocked
- [ ] Testing utilities set up
- [ ] First component test passes
- [ ] Test coverage configured
- [ ] Test scripts working in package.json

## Validation

### Test Framework Validation

```bash
# Run basic test suite
npm test

# Run tests in watch mode
npm run test:watch

# Check test coverage
npm run test:coverage

# Run specific test file
npx jest src/components/auth/__tests__/LoginForm.test.tsx
```

### Configuration Testing

```bash
# Verify Jest configuration
npx jest --showConfig

# Test if mocks work correctly
npm run build
npm run test

# Check for TypeScript errors
npx tsc --noEmit
```

Expected output:

- Jest runs without configuration errors
- Test files are discovered and executed
- Mocked DOM APIs work correctly
- Coverage reports are generated
- No TypeScript compilation errors

## Notes

- Consider using Vitest for faster test execution in development
- Add testing utilities for common patterns in your project
- Configure coverage thresholds based on project requirements
- Consider adding E2E testing with Playwright or Cypress for critical user flows
- Set up CI/CD integration for automated testing

## References

- [Testing Strategy](../../docs/testing-strategy.md)
- [Jest Documentation](https://jestjs.io/docs/getting-started)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro)
- [Testing Best Practices](../../docs/testing-best-practices.md)
