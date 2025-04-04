## Installing TypeScript

- Install globally with NPM:  `npm install -g typescript`
- Use the compiler:  `tsc`
- If installed locally:  `npx tsc`
## TSConfig Setup
- Initialize config file:  `tsc --init`
- `tsconfig.json` tells TypeScript how to compile the code   
- Command line flags can override settings
## Key Config Fields
#### target: "es5"
Determines the JavaScript version for output
#### module: "commonjs"
Sets the module system for the output
#### strict: true
Enables all strict type-checking options

**Includes:**
- `noImplicitAny`: Warns if a variable implicitly has the `any` type
- `strictNullChecks`: Warns if something might be `null` or `undefined`
- `noImplicitThis`: Requires type annotation for `this`
- `strictPropertyInitialization`: Ensures class properties are initialized
#### esModuleInterop: true
- Allows smooth import from both CommonJS and ES Modules
- Useful when working with NPM packages
#### skipLibCheck: true
- Skips type checking for files in `node_modules`
- Improves speed, but assumes those types are correct
#### forceConsistentCasingInFileNames: true
- Prevents issues with file name casing on case-sensitive systems
- Ensures import paths match actual file names exactly
