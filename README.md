# Project Network Tour of Data Sciences: 
## Flight network and airline alliances 

### REMOVE THE OVERLEAF LINK BEFORE SUBMITTING

Overleaf: https://www.overleaf.com/9477267966wjjtchkvnsnf  

### Abstract

We analyze the "Airline Route Mapper Route Database" which maps 3'321 airports (nodes) worldwide with their respective connections (67'663 edges) operated by 548 airlines. Some of these airlines have joined each other to form passenger airline alliances which for instance facilitates flight connections for multi stop flights. As of today three major airline alliances exist, **Star Alliance**, **Sky Team**, and **Oneworld**, which regroup 26, 20 and 14 airlines, respectively (state of 2014 to be consistent with the flight dataset). To aim of our project is to unravel the airline alliances network and their global presence in the air route network. We try to understand to what extent the whole flight network is dominated by flights belonging to the alliances and whether sparsely connected airports are equally likely to be served by alliances airlines than big hubs. Furthermore, we investigate whether the alliances operate in similar or different parts of the worlds, and based on this, which airlines are likely to join one, and which, of the alliances in the future. In addition, airlines within alliances tend to have agreements to avoid operating simultaneously between two airports, and based on this, we try to see whether there is an underlying network property which allows to identify the three major alliances without prior knowledge about their existence, and which airlines not yet belonging to them, are predisposed to join the alliance network. 

### Datasets

- The airport, airline and route data is available on [this website](https://openflights.org/data.html)

- The alliances dataset grouping the airlines to their alliance is derived from [here](https://www.hopper.com/articles/860/a-guide-to-the-three-major-airline-alliances-star-alliance-oneworld-and-sky-team)

### Research Questions

- **How prevalent are the alliances in the global flight route network?** (Marie)
     - For each alliance i, label the airports served by an alliance i flight, and compare the density of the alliance i airport network to the whole network density (check if the alliance network is connected, and maybe there are interesting relations between the big component/small components and the alliances), and do this analysis 3 times. Then do the same analysis but for all the alliances together. This should allow us to see how many airports are not served by alliance airlines, and what is the proportion of airports that are served by one alliance compared to airports served by 2 or all the alliances.
    
- **Is the alliance business a hub thing?** (Marie)
    - We label the airports by the number of alliances flights that serve it (0, 1, 2 or 3) and we analyze the correlation between this number and the degree of the airport. We expect that a lower degree airport is less likely to be connected to the alliance network than big hubs.
    - Case study on big cities which have multiple airports (e.g. London, Paris, Rome): is there a trend that only a few airports are served by alliance airports? If yes, then how does the correlation from the previous point change if we substract "the big city non-alliance airports", to get a better insight of the geographic expansion (vs. airport expansion) of the alliance network (maybe sth. to consider on the previous question as well).
    
- **Which part of the world is dominated by who, and what is a likely expansion?**
    - Each airline has a country of origin, and we can also associate each airport to a country. We then start the analysis by identifying the major alliance for each airport (for each airport count the number of edges for each alliance and attribute the airport to the alliance with the maximum count). We then have a graph with 3 labels, and nodes with an unknown label, if not served by an alliance company. A validation step of this approach is then to see whether the country of the airport is the same as the country of one of the airlines inside the alliance (some countries have airlines belonging to different alliances, but that should not matter). When plotting the result on the worldmap, we might see geographic differences between the alliances. 
    - We can study the expansion through transductive learning. In a first step we can unlabel some airports for which we know the major alliance serving it, and then through transductive learning, give labels to them and check the error. This can give an insight whether the current alliance status has an underlying network property. In a second step, through transductive learning, we can give labels to airports not served by an alliance airline. We could validate this step by checking airlines with country seat in the unlabelled airport countries (if there are any?) and see if between 2014 and now there were actual fusions or negotiations going on between these potential airlines and the alliances. 
    
- **Can the alliances be predicted from the construction of an airline network?**
    - We construct the airline network by giving different weights to the edges with respect to competitive alliances flights between two airports, and consecutive flights of the common alliance members. On this graph we see if we can cluster the airlines into the 3 major alliances (we probably tune the constructing weights parameters to make this happen). In this approach, we can also see if some airlines not yet part of an alliance are likely to become part of one. Again, we can validate that by checking recent fusions and negotiations. 
    - From this network, we could also check if we can identify the new alliances that formed (Vanilla Alliance, U-FLY Alliance, Value Aliance).





    
