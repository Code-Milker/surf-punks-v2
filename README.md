# Surf Punks V2
# SurfPunkV2 Smart Contract
## Overview
The `SurfPunkV2` contract is an ERC-721 compliant non-fungible token (NFT) implementation designed to capture the essence of surf culture in the digital realm. This contract facilitates the minting and management of unique "Surf Punk" NFTs, each representing a distinct digital surfer with its own identity and attributes. **Deployed on Ethereum Mainnet at contract address [0x5606447ca8f5f02b659203cc53f8aca1fbbe2c78](https://etherscan.io/token/0x5606447ca8f5f02b659203cc53f8aca1fbbe2c78), this collection features 1,000 planned SurfPunks, with 563 minted to date, held by 278 unique owners. View the live collection on [OpenSea](https://opensea.io/collection/surf-punks-nft-v2).**

## Features
1. **ERC-721 Compliance**: Inherits from OpenZeppelin's `ERC721`, ensuring standard NFT functionality and interoperability.
2. **Enumerable Tokens**: Implements `ERC721Enumerable` to allow enumeration of all tokens, facilitating easy tracking and management.
3. **URI Storage**: Utilizes `ERC721URIStorage` for flexible and modifiable token metadata storage, enabling dynamic updates to token information.
4. **Ownership Control**: Leverages `Ownable` to restrict certain functions to the contract owner, enhancing security and administrative control.
5. **Token Minting**: Includes a `mintTransfer` function that allows an authorized `mintvialAddress` to mint new tokens and assign them to a specified address.
6. **Randomization Integration**: Interacts with an external `SurfPunksRandomizer` contract to assign unique identifiers to tokens upon minting, ensuring each NFT is distinct.
7. **Base URI Management**: Provides functionality to set and lock the base URI for token metadata, ensuring consistency and preventing unauthorized changes.
8. **Contract Locking**: Once locked by the owner, certain contract parameters cannot be modified, enhancing security and immutability.
9. **Event Emission**: Emits `CloneXRevealed` events upon token minting, facilitating off-chain processes and integrations.

## Contract Details
- **Constructor**: Initializes the contract with the name "SurfPunkV2" and symbol "SurfPunkV2". The token ID counter starts at 1 to avoid using the default value of 0.
- **mintTransfer Function**: Restricted to the `mintvialAddress`, this function mints a new token, assigns it to the specified address, and interacts with the `SurfPunksRandomizer` to obtain a unique identifier for the token.
- **setRandomizerAddress Function**: Allows the contract owner to set the address of the `SurfPunksRandomizer` contract, enabling flexibility in updating the randomization logic.
- **setMintvialAddress Function**: Permits the contract owner to designate the authorized minting address, ensuring only approved entities can mint new tokens.
- **secureBaseUri Function**: Enables the owner to set the base URI for token metadata. This function can only be called if the contract is not locked, allowing updates to metadata storage paths when necessary.
- **lockContract Function**: Once invoked by the owner, it permanently locks the contract, preventing further changes to the base URI and enhancing the security and integrity of the token metadata.
- **tokensOfOwner Function**: Returns an array of token IDs owned by a specific address, aiding in token management and user interfaces by allowing users to view their holdings.
- **Overridden Functions**: Includes standard overrides for `_baseURI`, `_beforeTokenTransfer`, `_burn`, `tokenURI`, and `supportsInterface` to ensure compatibility and extend functionality as needed.

