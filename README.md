# smart-doc-manager
A document manager with automated metadata and tagging

## Project Setup

### Prerequisites
- Node.js (v14 or later)
- npm (v6 or later)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/SergKam/smart-doc-manager.git
   cd smart-doc-manager
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up Tailwind CSS:
   Follow the [official Tailwind CSS installation guide](https://tailwindcss.com/docs/guides/nextjs) for Next.js.

4. Configure TypeORM with SQLite:
   - Create a `ormconfig.json` file in the root directory with the following content:
     ```json
     {
       "type": "sqlite",
       "database": "database.sqlite",
       "synchronize": true,
       "entities": ["src/models/**/*.ts"]
     }
     ```

5. Set up ESLint and Prettier:
   - Create a `.eslintrc.js` file with the following content:
     ```javascript
     module.exports = {
       parser: '@typescript-eslint/parser',
       extends: [
         'plugin:react/recommended',
         'plugin:@typescript-eslint/recommended',
         'prettier',
         'plugin:prettier/recommended'
       ],
       settings: {
         react: {
           version: 'detect'
         }
       },
       rules: {}
     };
     ```
   - Create a `.prettierrc` file with the following content:
     ```json
     {
       "singleQuote": true,
       "trailingComma": "all"
     }
     ```

6. Set up logging with Winston:
   - Create a `logger.ts` file in the `src/utils` directory with the following content:
     ```typescript
     import { createLogger, format, transports } from 'winston';

     const logger = createLogger({
       level: process.env.LOG_LEVEL || 'info',
       format: format.combine(
         format.colorize(),
         format.timestamp(),
         format.printf(({ timestamp, level, message }) => {
           return `${timestamp} [${level}]: ${message}`;
         })
       ),
       transports: [new transports.Console()]
     });

     export default logger;
     ```

7. Start the development server:
   ```bash
   npm run dev
   ```

### Testing
- Ensure the development server starts without errors.
- Verify that Tailwind CSS classes work.
- Test TypeORM connection to SQLite.
- Verify that logging works with different log levels.
