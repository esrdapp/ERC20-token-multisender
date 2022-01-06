# ERC20-token-multisender

Allows you to batch transfer ERC20 tokens to multiple addresses.

When you first deploy the smart contract, you need to provide the ERC20 token address of the token that you will ultimately be batch transferring.

Once deployed, send your tokens to the smart contract.

You can now batch transfer them to multiple addresses, each with specifc amounts.

When calling the batchTransfer function, both the addresses and the amounts, need to be provided as arrays.

For example, 

tokenHolders:
you would provide the following array inside square brackets, including the quotation marks and commas.
["0xaddress1", "0xaddress2", "0xaddress3", "0xaddress4", "0xaddress1"]

amounts:
you would provide the following
["25", "72", "14", "55", "43"]

By doing this, 0xaddress1 would receive 25 tokens, 0xaddress1 would receive 72 tokens, and so on.

Please also be careful regarding the token decimals!!

The example above is based on a token with 0 decimals.

If your token is standard 18 decimals ERC20 token, and you wanted to send 25 tokens, you would in fact
need to send the following, based on the example above:

["25000000000000000000", "72000000000000000000", "14000000000000000000", "55000000000000000000", "43000000000000000000"]

If the token was to 9 decimals, then it would be:

["25000000000", "72000000000", "14000000000", "55000000000", "43000000000"]

If at any point to simply want to withdraw any leftover tokens, you can call the "withDrawToken" function

The number of token transfers you can send in a single function call, is highly dependent on the blockchain you are deploying to.

For example, if using this on the XDai chain, you can safely send 150 batch transfers at once, but for other chains it will be less, or possibly more.

Gas costs will of course be dependent on the number of transfers you make per call.
