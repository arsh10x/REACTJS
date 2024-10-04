## Bundler

**Definition**: A tool that packages JavaScript and other assets for deployment.

### Popular options:
- Webpack.
- Rollup.
- Parcel.

### Features:
- Code splitting.
- Minification.
- Tree shaking (dead code elimination).
- Asset optimization.

### Example (basic Webpack config):
```javascript
module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader'
        }
      }
    ]
  }
};
```

---