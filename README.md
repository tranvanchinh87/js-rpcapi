const { mpapi } = require('mpapi');

// Connect to node
mpapi.node.setProvider("http://127.0.0.1:8732");
mpapi.node.setDebugMode(true);

1. Create new account
// Generate seed phrase
const mnemonic = module.exports.mpapi.crypto.generateMnemonic();
// Generate new keys of account
const keys = module.exports.mpapi.crypto.generateKeys(mnemonic);

2. Get existing account by private key
const extractedKeys = module.exports.mpapi.crypto.extractKeys('edsk3uku2wuuMztoazUmusXoRgFYRJyPyN9QYdoPDZo6JEKM3QMd5t');

3. Get plex_balance
const plex_balance = utility.totez(await module.exports.mpapi.rpc.getPlexBalance(extractedKeys.pkh));)

4. Get mine_balance
const mine_balance = utility.totez(await module.exports.mpapi.rpc.getMineBalance(extractedKeys.pkh));

5. Send mine to another account
const operations = await module.exports.mpapi.rpc.mine_transfer(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1MN1YB8ofoZokHyUAmH9oYKfxEHqF1XkT7', // Receiver
  100, // Amount of mine
  1 // Default fee
);

6. Send plex to another account
const operations = await module.exports.mpapi.rpc.plex_transfer(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1MN1YB8ofoZokHyUAmH9oYKfxEHqF1XkT7', // Receiver
  100, // Amount of plex
  1 // Default fee (mine value)
);

7. Set delegate
const operations = await module.exports.mpapi.rpc.setDelegate(
  extractedKeys.pkh, 
  extractedKeys, 
  'mp1FCcGeqnRG2wawPaerF7JbY8EQ8dvm8wig', // Delegate address
  1 // Default fee
);

8. Undelegate
const operations = await module.exports.mpapi.rpc.setDelegate(
  extractedKeys.pkh, 
  extractedKeys, 
  undefined, 
  1 // Default fee
);

9. Looging for operation in blocks 
const blockHash = await module.exports.mpapi.rpc.findOperation(
  'oo7D7FnyLeDL9VCNiXWY9cty8MvTzX8HDSGmuqGDfSNSwnwLogm',
  50 // Count blocks ago
);

10. Get price of plex for one mine
const pricePlex = await getPricePlexForOneMine()

11. Get price of mine for one plex
const priceMine = await getPriceMineForOnePlex()

12. Example of catching errors
try {
  const blockHash = await module.exports.mpapi.rpc.findOperation(
    'oo7D7FnyLeDL9VCNiXWY9cty8MvTzX8HDSGmuqGDfSNSwnwLogm',
    2
  );
} catch (error) {
  console.log(error)
}

