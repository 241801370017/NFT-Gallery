// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract NFTGallery {
    struct NFT {
        uint id;
        string name;
        string uri;
        address owner;
    }

    uint public nextId = 1;
    mapping(uint => NFT) public nfts;
    mapping(address => uint[]) public owned;

    event Created(uint id, string name, string uri, address owner);

    function create(string memory name, string memory uri) public {
        nfts[nextId] = NFT(nextId, name, uri, msg.sender);
        owned[msg.sender].push(nextId);
        emit Created(nextId++, name, uri, msg.sender);
    }

    function getOwned(address user) public view returns (uint[] memory) {
        return owned[user];
    }
    ##contract
    "C:\Users\ALEKHYA\Pictures\Screenshots\Screenshot 2025-09-10 142504.png"
