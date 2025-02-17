# NETWORK-LEVEL DATA
All instances are based on the same physical network. 
Data regarding that network can be found in the files in the network_data folder.
Those files are as follows:
network_data/network_terminals.txt: Lists the terminals that are in the network
network_data/network_legs.txt: Lists the possible terminal to terminal moves in the network
network_data/network_paths.txt: Lists the path taken by all shipments that share a common origin and destination terminal

See the headers of those files for detailed information regarding their contents

# INSTANCE-LEVEL DATA
Given the network defined in the files in the network_data folder an instance consists of two additional files whose names observe the following format:
1) inst_\vert K \vertcommods_\rho_commodities_XXX.txt
2) inst_\vert K \vertcommods_\rho_scenarios_XXX.txt

where 
\vert K \vert takes on one of the values 100,150,200,250,300,350,400,450,500,550,600,650,700,750
\rho takes on one of the values 6,12,18,24,30,36,42,48
XXX takes on one of the values 1,2,3,4,5

The first file lists the commodities for an instance. 
It contains lines that list the following information for each commodity 
Origin,Destination,Avail,Due
where Avail and due are quoted in terms of periods that represent 30 minute intervals.
In the notation of the paper this file contains a line for each commodity $k$ that consists of
o_k,d_k,e_k,l_k

The second file lists the fraction of vehicle capacity (q_k/u_{ij} in the notation of the paper) required for each commodity. These instances are based on a homogenous fleet so u_{ij} = u for all legs (i,j). 
All sizes are on a single line, with the first character in the line always equaling 1 (the probability of these sizes occurring) and the sizes then listed,space-delimited, in the same order the commodities appear in the corresponding commodities file. 

As an example, to construct the 2nd instance with 300 commodities and \rho = 36 one should read the files
1) inst_300commods_36_2_commodities.txt to get the commodities in the instance
2) inst_300commods_36_2_scenarios.txt to get their sizes.

In the inst_300commods_36_2_commodities.txt file the first non-header line is
MTG,MIA,42,145
which indicates a commodity that originates in terminal MTG at time period 42 that requires transportation to terminal MIA by time period 145
The corresponding scenarios file indicates that commodity occupies 0.6065239063019752 of vehicle capacity. 
The file network_data/network_paths.txt has the line
MTG,MIA,MTG,JAX,MIA
which indicates that this shipment travels on the path (v_1^k,v_2^k,v_3^k) = (MTG,JAX,MIA)


