## Chunking

**Definition**: Breaking down the application bundle into smaller chunks.

### Implementation:
Usually handled by bundlers like Webpack.

### Benefits:
- Allows for more efficient loading and caching of application parts.

### Example (Webpack config):
```javascript
module.exports = {
  entry: {
    main: './src/main.js',
    vendor: './src/vendor.js'
  },
  output: {
    filename: '[name].[chunkhash].js',
    path: path.resolve(__dirname, 'dist')
  }
};
```

---