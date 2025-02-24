---
# Debt Auction Lot Size Increase

>**Alias:  
>**Parameter Name: `pad`  
>**Containing Contract: Flopper  
>**Scope: System  
>**Technical Docs: https://docs.makerdao.com/smart-contract-modules/system-stabilizer-module/flop-detailed-documentation

## Description
Debt Auctions are used to recapitalize the system by minting and auctioning off MKR for a fixed amount of DAI. In this process, keepers bid on how little MKR they are willing to accept for the fixed Dai amount they have to pay at auction settlement. The starting amount of MKR in these auctions is determined by the `Debt Auction Initial Lot Size` parameter. Auction participants may bid a lower amount of MKR than the initial lot size. If there are no bids, they must wait for the duration of the auction before the auction can be restarted with a higher `Debt Auction Initial Lot Size`. This increase is determined by the `Debt Auction Lot Size Increase` parameter. 

## Example
If the `Debt Auction Initial Lot Size` is 100 MKR and the `Debt Auction Lot Size Increase` is 50%, then an auction that is restarted due to no bids can have an initial bid not exceeding 150 MKR. If there are still no bids, the auction can be restarted again with an initial bid not exceeding 225 MKR.


## Purpose
Changing the `Debt Auction Lot Size Increase` parameter allows Maker Governance to minimize the total MKR minted by ensuring competitive auctions and minimizing gas costs for auction participants. 


## Trade-offs
A small `Debt Auction Lot Size Increase` would result in auctions having to be restarted (`kicked`) many times before they become interesting to keepers. This would result in the protocol remaining undercollateralized for a long period and also result in additional gas costs due to multiple restarts.
	
A large `Debt Auction Lot Size Increase` could result in large amounts of MKR minted if there are insufficient participants in the auctions. On the other hand, if there are sufficient participants, a sufficiently large `Debt Auction Lot Size Increase` would ensure that auctions do not need to be restarted multiple times. This saves gas costs for keepers and keeps the protocol in an undercollateralized state for a shorter duration.  


## Changes
Adjusting the `Debt Auction Lot Size Increase` parameter is a manual process that requires an executive vote. Changes to the `Debt Auction Lot Size Increase` are subject to the GSM Pause Delay.

**Why increase this parameter?**
Maker Governance may wish to increase the `Debt Auction Lot Size Increase` if debt auctions have to be repeated restarted before keepers are able to submit profitable bids.

**Why decrease this parameter?**
Maker Governance may wish to decrease the `Debt Auction Lot Size Increase` if there is a risk of insufficient keeper participation resulting in a risk of high amounts of MKR being minted.


## Considerations
This parameter should be tuned in conjunction with the `Debt Auction Initial Lot Size` parameter, which has similar consequences when increased or decreased as the `Debt Auction Lot Size Increase` parameter.

>Page last reviewed: -  
>Next review due: -  

