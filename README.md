# Project Network Tour of Data Sciences
## Title: Flight network and airline alliances

Github repository of the final project of the class *EE-558, A Network Tour of Data Science, EPFL*. This readme contains an abstract with our problem definition, the datasets we used to analyze the problem and the different research questions we tackle. The code is found in the jupyter notebook `main_analysis.ipynb`. The libraries needed are listed below.

### Libraries used
We used the following libraries for this project, with Python 3.6.5


 Computational:

    numpy (as np)
    pandas (pd)
    networkx (nx)

Graphical:

    seaborn (as sns) (version 0.9.0)
    matplotlib (as plt)
    folium


### Abstract

We analyze the "Airline Route Mapper Route Database" which maps 3'321 airports (nodes) worldwide with their respective connections (67'663 edges) operated by 548 airlines. Some of these airlines have joined each other to form passenger airline alliances which for instance facilitates flight connections for multi stop flights. As of today three major airline alliances exist, **Star Alliance**, **Sky Team**, and **Oneworld**, which regroup 26, 20 and 14 airlines, respectively (state of 2014 to be consistent with the flight dataset). To aim of our project is to unravel the airline alliances network and their global presence in the air route network. We try to understand to what extent the whole flight network is dominated by flights belonging to the alliances and whether sparsely connected airports are equally likely to be served by alliances airlines than big hubs. Furthermore, we investigate whether the alliances operate in similar or different parts of the worlds, and based on this, which airlines are likely to join one, and which, of the alliances in the future. In addition, airlines within alliances tend to have agreements to avoid operating simultaneously between two airports, and based on this, we try to see whether there is an underlying network property which allows to identify the three major alliances without prior knowledge about their existence, and which airlines not yet belonging to them, are predisposed to join the alliance network.

### Datasets

- The airport, airline and route data is available on [this website](https://openflights.org/data.html)

- The alliances dataset grouping the airlines to their alliance is derived from [here](https://www.hopper.com/articles/860/a-guide-to-the-three-major-airline-alliances-star-alliance-oneworld-and-sky-team)

### Research Questions

- **How prevalent are the alliances in the global flight route network?**
     Create a subnetwork for each individual alliance, which integrates all the edges/flights and nodes/airports that are flown and served, respectively, by an alliance airline member. Analyse the network properties and do comparisons between each alliance subnetwork, the whole alliance network and the whole flight network.

- **Is the alliance business a hub thing?**
    We label the airports by the number of alliances flights that serve it (0, 1, 2 or 3) and we analyze the correlation between this number and the degree of the airport. We expect that a lower degree airport is less likely to be connected to the alliance network than big hubs.

- **Which part of the world is dominated by who, and what is a likely expansion?**
     - **Geographic distribution of the alliances**:
Each airline has a country of origin, and we can also associate each airport to a country. We then start the analysis by identifying the major alliance for each airport (for each airport count the number of edges for each alliance and attribute the airport to the alliance with the maximum count, in case of a tie, the airport is labelled by the two or three major alliances). We then have a graph with 3 labels, and nodes with an unknown label, if not served by an alliance company. A validation step of this approach is then to see whether the country of the airport is the same as the country of one of the airlines inside the alliance. When plotting the result on the worldmap, we might see geographic differences between the alliances.

    - **Airport expansion of the alliances predicted through label propagation**:
We study the expansion of the alliances through label propagation. The underlying concept is that airport not yet served by an alliance will be served by the alliance occurring with the highest frequency among its neighbours. Each neighbour has one vote, independent of how connected it is, and an airport may be labelled by 2 or 3 alliances if there is a tie among the node degree between the alliances (at the step of the initial labelling) or a tie between the vote comparison (at the step of attributing the label) (see illustration below).
In a first step we validate our algorithm by only working on the alliance network and by randomly unlabelling half of the nodes for which we know the major alliance serving it. This allows us to get some accuracy scores and to see if our algorithm is valid. In a second step, we keep all the airports labelled which are served by an alliance and through label propagation we predict the likely alliance expansion (we predict a label for all the airports inside our largest connected component).

- **Can the alliances be predicted from the construction of an airline network?**
    - We construct an airline network by giving different weights to the edges with respect to consecutive flights of the common alliance members. On this graph we see if we can cluster the airlines into the 3 major alliances (we probably tune the constructing weights parameters to make this happen). In this approach, we can also see if some airlines not yet part of an alliance are likely to become part of one. 


## Authors

* *Gabor Csordas*
* *Nicolas Fontbonne*
* *Maëlle Le Clainche*
* *Marie Sadler*


## License

MIT License

Copyright (c) 2019 Gabor Csordas, Nicolas Fontbonne, Maëlle Le Clainche, Marie Sadler

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
