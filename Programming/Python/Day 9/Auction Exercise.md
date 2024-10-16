# Basic Program Flow:

![](Pictures/Auction%20Exercise%20-%20Basic%20Program%20Flow.png)

# Data Structure

We will need to decide on how best to store the information.

We need to store:

- Bidder's **Name**
- Bidder's **Bid**

Do we store this in a 2 dimensional array? A dictionary with a nested list or dictionary?

A simple solution my be to just store the bidder's name as the **Key** and their bid as the **Value**.

```python
bids = {
	"Bidder": Bid
	"Bidder2": Bid2	
}
```

We can then iterate over the dictionary to find the highest bid:

```python
highest_bid = 0
for bid in bids:
	if bids[bid] > highest_bid:
		highest_bid = bids[bid]
```