# Template: Launcher

![Static Badge](https://img.shields.io/badge/progress-complete-green?style=for-the-badge) ![Static Badge](https://img.shields.io/badge/template-%23fcc603?style=for-the-badge&labelColor=%23fcc603) ![Static Badge](https://img.shields.io/badge/gfebs-%23737373?style=for-the-badge&labelColor=%23fcc603)

Internal boilerplate for creating GFEBs DL launcher packages.

## Demo

Insert gif or link to demo

## New GFEBS Product

To create a new GFEBS DL Product, install `template-training-content` with [Github CLI](https://cli.github.com/)

```bash
gh repo create [COURSE_CODE]-launcher --template="aretum-eagleharbor-gfebs/template-launcher"

cd [COURSE_CODE]-launcher

npm i -D
```

## Contributing

To contribute and make edits to `template-training-content`, clone the project

```bash
git clone https://github.com/aretum-eagleharbor-gfebs/template-launcher.git
```

Go to the project directory

```bash
cd template-launcher
```

Install dependencies

```bash
npm install
```

Compile and Hot-Reload for Development

```bash
npm run dev
```

Compile and Minify for Production

```bash
npm run build
```

## Running Tests

To run tests, run the following command

```bash
npm run test
```

## Tech Stack

**Client:** Vue, Selenium, Sass, TailwindCSS

**Server:** Node
