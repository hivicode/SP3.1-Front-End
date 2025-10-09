# Commit Messages untuk SP3.1 Front End

## Commit Messages yang Direkomendasikan

### 1. Initial Commit
```bash
git commit -m "feat: initial project setup with JavaScript learning materials

- Add pertemuan_3: arrays, conditionals, and loops examples
- Add pertemuan_4: functions, modules, and practical exercises
- Include CRUD application for barang management
- Add ES6 modules examples with import/export"
```

### 2. Documentation Update
```bash
git commit -m "docs: add comprehensive README files

- Add main README with project overview and structure
- Add pertemuan_3 README covering arrays, conditionals, loops
- Add pertemuan_4 README covering functions, modules, exercises
- Include code examples and usage instructions
- Add prerequisites and setup requirements"
```

### 3. Alternative Commit Messages (Jika commit terpisah)

#### Untuk pertemuan_3:
```bash
git commit -m "feat(pertemuan_3): add JavaScript fundamentals examples

- Array operations: create, read, update, delete
- Conditional statements: if/else, switch-case, ternary
- Loop structures: for, while, do-while, forEach
- Nested conditions and loops examples"
```

#### Untuk pertemuan_4:
```bash
git commit -m "feat(pertemuan_4): add functions and modules examples

- Arrow functions with parameters and callbacks
- Rest parameters and function overloading
- ES6 modules with import/export
- CRUD application for practical learning
- Math calculations with modular structure"
```

#### Untuk documentation:
```bash
git commit -m "docs: add detailed README documentation

- Project structure and learning path
- Code examples and syntax references
- Setup instructions for ES6 modules
- Prerequisites and technology stack"
```

## Cara Menggunakan

1. **Untuk commit pertama (semua file):**
   ```bash
   git add .
   git commit -m "feat: initial project setup with JavaScript learning materials

   - Add pertemuan_3: arrays, conditionals, and loops examples
   - Add pertemuan_4: functions, modules, and practical exercises
   - Include CRUD application for barang management
   - Add ES6 modules examples with import/export"
   ```

2. **Untuk commit dokumentasi:**
   ```bash
   git add README.md pertemuan_3/README.md pertemuan_4/README.md
   git commit -m "docs: add comprehensive README files

   - Add main README with project overview and structure
   - Add pertemuan_3 README covering arrays, conditionals, loops
   - Add pertemuan_4 README covering functions, modules, exercises
   - Include code examples and usage instructions
   - Add prerequisites and setup requirements"
   ```

## Convention yang Digunakan

- **feat**: New feature or functionality
- **docs**: Documentation changes
- **fix**: Bug fixes
- **refactor**: Code refactoring
- **style**: Code style changes
- **test**: Adding or updating tests

Setiap commit message mengikuti conventional commits format dengan deskripsi yang jelas dan detail perubahan yang dilakukan.
