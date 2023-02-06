# Path Registry Standard

| Status        | Proposed |
:-------------- |:---------------------------------------------------- |
| **FLIP #**    | [636](https://github.com/onflow/flow/pull/636)                                                                                       |
| **Author(s)** | Glaicon Peixer (gjpeixer@gmail.com), Felipe Ribeiro (X), Brian Dilley (x)                                                            |
| **Sponsor**   | X (X@dapperlabs.com)                                                                                                                 |
| **Updated**   | 2023-02-05                                                                                                                           |


## Objective

This proposal will make it possible to manage paths used through the network. 
Using this standard you won't need to be concern about path conflict with other smart contracts, just call the PathRegistry and get your custom path completly unique for your smart contract. If you need get Path informations about a smart contract, call getPaths and you will be able to get that.

## Motivation

Currently there is no standard for avoid path conflict between smart contracts. The best we can 
find is a recomendation to create a name path more specific. Although it is a open framework 
where the smart contract authors can find a freedom to create their pattern.

## User Benefit

We feel that a pattern that authors can implement that allows more confidence to create new
smart contracts without having to worry about path conflicts will have a better ux.

## Design Proposal

The core of this proposal is to add these call on init function
```
  init() {

    let contractPath = PathRegistry.createContractPath(contract: Type<TopShot>(), "TopShotCollection")
    // Paths
    self.collectionPublicPath = contractPath.collectionPublicPath
    self.collectionStoragePath = contractPath.collectionStoragePath
    self.collectionPrivatePath = contractPath.collectionPrivatePath
    ...
  }
```

## Drawbacks

NO IDEA

## Alternatives Considered

NO IDEA

## Performance Implications

As the use of this pattern must be enforced within the init function, we don't believe it causes any performance issues.

## Dependencies

NO IDEA

## Engineering Impact

Any new smart contract should have to use this standard. We will be able to add past contracts in order to have the current smart contracts.

## Best Practices

NFT authors should do their best to implement as many views from the standard metadata set as appropriate for 
their application. 

NFT authors should document the views they support and contract creators should document the views they require. 
It could be worth exploring a design-by-contract paradigm to formalize this in a forthcoming FLIP.

## Tutorials and Examples

NO YET

### Example 1

The Find project is going to be using metadata as lookup and index points. The project is available here:
https://github.com/findonflow/find

### Example 2

This example shows how you might implement this specification with the ability to add new view types to your NFT 
contract after it has already been published through the use of a `ViewResolver` pattern.
[Gist available here](https://gist.github.com/briandilley/962e94682b7945d882fcd99702011ea4),
[Playground available here](https://play.onflow.org/a71203b9-a03a-47f9-ab70-7285fcf4c56a?type=account&id=0)

## Compatibility

It would be available to all smart contract.

## User Impact

This feature can be rolled out with no fear of changes to the user. However documentation should be provided on how 
they can change their contracts and add views. 

## Related Issues

NO IDEA

## Prior Art

None

## Questions and Discussion Topics

NO IDEA