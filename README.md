const { mpapi } = require('mpapi');

// Connect to 
<pre><code>
mpapi.node.setProvider("http://127.0.0.1:8732");
mpapi.node.setDebugMode(true);
</code></pre>

1. Create new account
<pre><code>
// Generate seed phrase
const mnemonic = module.exports.mpapi.crypto.generateMnemonic();
// Generate new keys of account
const keys = module.exports.mpapi.crypto.generateKeys(mnemonic);
</code></pre>

2. Get existing account by private key
<pre><code>
const extractedKeys = module.exports.mpapi.crypto.extractKeys('edsk3uku2wuuMztoazUmusXoRgFYRJyPyN9QYdoPDZo6JEKM3QMd5t');
</code></pre>

3. Get plex_balance
<pre><code>
const plex_balance = utility.totez(await module.exports.mpapi.rpc.getPlexBalance(extractedKeys.pkh));)
</code></pre>

4. Get mine_balance
<pre><code>
const mine_balance = utility.totez(await module.exports.mpapi.rpc.getMineBalance(extractedKeys.pkh));
</code></pre>

5. Send mine to another account
<pre><code>
const operations = await module.exports.mpapi.rpc.mine_transfer(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1MN1YB8ofoZokHyUAmH9oYKfxEHqF1XkT7', // Receiver
  100, // Amount of mine
  1 // Default fee
);
</code></pre>

6. Send plex to another account
<pre><code>
const operations = await module.exports.mpapi.rpc.plex_transfer(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1MN1YB8ofoZokHyUAmH9oYKfxEHqF1XkT7', // Receiver
  100, // Amount of plex
  1 // Default fee (mine value)
);
</code></pre>

7. Set delegate
<pre><code>
const operations = await module.exports.mpapi.rpc.setDelegate(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1FCcGeqnRG2wawPaerF7JbY8EQ8dvm8wig', // Delegate address
  1 // Default fee
);
</code></pre>

8. Undelegate
<pre><code>
const operations = await module.exports.mpapi.rpc.setDelegate(
  extractedKeys.pkh, 
  extractedKeys, 
  undefined, 
  1 // Default fee
);
</code></pre>

9. Looging for operation in blocks
<pre><code>
const blockHash = await module.exports.mpapi.rpc.findOperation(
  'oo7D7FnyLeDL9VCNiXWY9cty8MvTzX8HDSGmuqGDfSNSwnwLogm',
  50 // Count blocks ago
);
</code></pre>

10. Get price of plex for one mine
<pre><code>
const pricePlex = await getPricePlexForOneMine()
</code></pre>

11. Get price of mine for one plex
<pre><code>
const priceMine = await getPriceMineForOnePlex()
</code></pre>

12. Example of catching errors
<pre><code>
try {
  const blockHash = await module.exports.mpapi.rpc.findOperation(
    'oo7D7FnyLeDL9VCNiXWY9cty8MvTzX8HDSGmuqGDfSNSwnwLogm',
    2
  );
} catch (error) {
  console.log(error)
}
</code></pre>
