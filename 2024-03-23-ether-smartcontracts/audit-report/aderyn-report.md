# Aderyn Analysis Report

This report was generated by [Aderyn](https://github.com/Cyfrin/aderyn), a static analysis tool built by [Cyfrin](https://cyfrin.io), a blockchain security company. This report is not a substitute for manual audit or security review. It should not be relied upon for any purpose other than to assist in the identification of potential security vulnerabilities.
# Table of Contents

- [Summary](#summary)
  - [Files Summary](#files-summary)
  - [Files Details](#files-details)
  - [Issue Summary](#issue-summary)
- [Medium Issues](#medium-issues)
  - [M-1: Centralization Risk for trusted owners](#m-1-centralization-risk-for-trusted-owners)
  - [M-2: Using `ERC721::_mint()` can be dangerous](#m-2-using-erc721mint-can-be-dangerous)
- [Low Issues](#low-issues)
  - [L-1: PUSH0 is not supported by all chains](#l-1-push0-is-not-supported-by-all-chains)
- [NC Issues](#nc-issues)
  - [NC-1: Functions not used internally could be marked external](#nc-1-functions-not-used-internally-could-be-marked-external)


# Summary

## Files Summary

| Key | Value |
| --- | --- |
| .sol Files | 1 |
| Total nSLOC | 0 |


## Files Details

| Filepath | nSLOC |
| --- | --- |
| **Total** | **0** |


## Issue Summary

| Category | No. of Issues |
| --- | --- |
| Critical | 0 |
| High | 0 |
| Medium | 2 |
| Low | 1 |
| NC | 1 |


# Medium Issues

## M-1: Centralization Risk for trusted owners

Contracts have owners with privileged rights to perform admin tasks and need to be trusted to not perform malicious updates or drain funds.

- Found in src/eReais.sol [Line: 10](src\eReais.sol#L10)

	```solidity
	contract eReais is ERC20, ERC20Burnable, ERC20Pausable, AccessControl {
	```

- Found in src/eReais.sol [Line: 36](src\eReais.sol#L36)

	```solidity
	    function pause() public onlyRole(PAUSER_ROLE) {
	```

- Found in src/eReais.sol [Line: 40](src\eReais.sol#L40)

	```solidity
	    function unpause() public onlyRole(PAUSER_ROLE) {
	```

- Found in src/eReais.sol [Line: 44](src\eReais.sol#L44)

	```solidity
	    function issue(address to, uint256 amount) public onlyRole(MINTER_ROLE) {
	```

- Found in src/eReais.sol [Line: 49](src\eReais.sol#L49)

	```solidity
	    function redeem(uint256 amount) public onlyRole(BURNER_ROLE) {
	```

- Found in src/eReais.sol [Line: 60](src\eReais.sol#L60)

	```solidity
	    ) public onlyRole(COMPLIANCE_ROLE) {
	```

- Found in src/eReais.sol [Line: 66](src\eReais.sol#L66)

	```solidity
	    ) public onlyRole(COMPLIANCE_ROLE) {
	```



## M-2: Using `ERC721::_mint()` can be dangerous

Using `ERC721::_mint()` can mint ERC721 tokens to addresses which don't support ERC721 tokens. Use `_safeMint()` instead of `_mint()` for ERC721.

- Found in src/eReais.sol [Line: 46](src\eReais.sol#L46)

	```solidity
	        _mint(to, amount);
	```



# Low Issues

## L-1: PUSH0 is not supported by all chains

Solc compiler version 0.8.20 switches the default target EVM version to Shanghai, which means that the generated bytecode will include PUSH0 opcodes. Be sure to select the appropriate EVM version in case you intend to deploy on a chain other than mainnet like L2 chains that may not support PUSH0, otherwise deployment of your contracts will fail.

- Found in src/eReais.sol [Line: 2](src\eReais.sol#L2)

	```solidity
	pragma solidity 0.8.20;
	```



# NC Issues

## NC-1: Functions not used internally could be marked external



- Found in src/eReais.sol [Line: 36](src\eReais.sol#L36)

	```solidity
	    function pause() public onlyRole(PAUSER_ROLE) {
	```

- Found in src/eReais.sol [Line: 40](src\eReais.sol#L40)

	```solidity
	    function unpause() public onlyRole(PAUSER_ROLE) {
	```

- Found in src/eReais.sol [Line: 44](src\eReais.sol#L44)

	```solidity
	    function issue(address to, uint256 amount) public onlyRole(MINTER_ROLE) {
	```

- Found in src/eReais.sol [Line: 49](src\eReais.sol#L49)

	```solidity
	    function redeem(uint256 amount) public onlyRole(BURNER_ROLE) {
	```

- Found in src/eReais.sol [Line: 53](src\eReais.sol#L53)

	```solidity
	    function isBlacklisted(address _address) public view returns (bool) {
	```

- Found in src/eReais.sol [Line: 57](src\eReais.sol#L57)

	```solidity
	    function blacklistAddress(
	```

- Found in src/eReais.sol [Line: 64](src\eReais.sol#L64)

	```solidity
	    function destroyBlackFunds(
	```


