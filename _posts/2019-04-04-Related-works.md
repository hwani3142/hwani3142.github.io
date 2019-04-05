---
title: "Related works"
date: 2019-04-04 18:00:00 -0400
categories: jekyll update
---
# LSM-tree & NVRAM Related works 

## Design and optimize LSM-tree 

1. bLSM
	- Analyze write and read amplification of LSM-tree in practical terms 
		- Improve these problems implementing merge scheduler, using bloom filter respectively.

		2. LSM-trie
			- Design trie structure-based LSM-tree using hash to reduce write amplification 
				- Target to small key-value entry
					- Use clustering method to bloom filter for efficient access 

					3. WiscKey
						- Separate value from key in LSM-tree
							- While value is stored into value-log, key and value offset are inserted into LSM-tree.
								- Minimize write amplification using key-only compaction and garbage collection on value-log

								4. Optimization of Space amplification in RocksDB
									- Present key techniques such as effective compression, dynamic level size setting to reduce storage usage in RocksDB
										- Analyze the characteristics at each level such as the amount of disk write, the number of data compactions, location of the desired data during read operation, and so on in RocksDB

										5. Optimization of RocksDB for Redis on Flash
											- In order to cope with growing data size in Redis that is a popular in-memory database system, present RocksDB combined with Redis
												- Analyze major parameters of affecting performance on RocksDB
													

## Data compaction mechanism

												1. dCompaction
													- Minimize write overhead on data compaction using new compaction logic that delay physical write and store parent files number to seek real physical data from them
														- For improving performance, also define trigger conditions of real or virtual compaction 
															  
														2. Lightweight compaction
															- Similarly, present compaction methodology that merge only metadata among compaction candidate files

															3. Pipelined compaction
																- Focus on the computation overhead on data compaction
																	- Analyze the compaction procedure and apply the parallelism of CPU, I/O devices to that using pipeline method.
																	  

## LSM with NVM
																	1.  *Redesigning LSMs for Nonvolatile Memory with NoveLSM*
																	- 특징
																		- Shows why LSM needs to utilize NVM-based design
																			- To exploit NVM's Byte-addressability in hybrid DRAM and NVM environment, implement NoveLSM design such as
																					- DRAM-memtable & NVM-immutable memtable structure
																							- In both DRAM and NVM, memtable & immutable memtable structure
																								- Reduce recovery cost with in-place updates
																									- Eliminates logging about in-memory data
																										- Parallelizing read operation with additional threads
																											- Reducing data serialization/deserialization and compaction cost
																												- Compaction 
																												- 차이점
																													- Since LSM-tree has mainly bottleneck during on-disk compaction , We focus on compaction across levels on-disk
																														- We consider sequential-copy to NVM as well as sequential-write to disk
																															- We address some design policies for applying to various applications

																															2. *Rethinking DRAM caching for LSMs in an NVRAM Environment*
																															- 특징
																																- Analyze of DRAM caching cost in LSM-tree
																																	- Implement pmemenv that stores persistent-pool-based SST format
																																		- Apply 2Q cache policy to DRAM-NVRAM hybrid environment

																																		- 차이점
																																			- We present efficient architecture replacing block-based file format and exploit byte-addressability of NVM
																																				- [PROGRESS] Also, we implement cache that can operate in our design efficiently 

																																				3. NVMRocks
																																				- 특징
																																					- Implement NVM-aware RocksDB system such as NVM-allocator, file system, multi-tiered cache using NVM
																																						- Implement persistent memtable structure that remove logging overhead and ensure persistence of memtable
																																							- Also, mention need of redesigning on-disk data structure with NVM to optimize NVM-aware system

																																							4. SLM-DB
																																							- 특징
																																								- 

## Application of NVRAM 
### Data structure
																																								1. HiKV

																																								2. Failure-atomic Slotted paging

																																								3. FP-tree

																																								4. WORT

																																								5. A Write-friendly and Cache-optimized Hashing Scheme for Non-volatile Memory Systems



### File-system


### Database recovery 

																																								1. Write-Behind Logging
																																									- Propose the new logging protocol utilizing NVRAM 

																																									2. NVWAL: Exploiting NVRAM in Write-Ahead Logging

																																									5. 
