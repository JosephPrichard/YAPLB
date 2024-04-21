# Sliding Puzzle Benchmarks

Benchmarking implementations of sliding puzzle solvers [sliding puzzle problem](https://en.wikipedia.org/wiki/15_puzzle) using the AStar algorithm in various languages.
Each implementation is guaranteed to find the shortest number of steps to solve any solvable NPuzzle. 

The sliding puzzle problem is a space-exploration problem involving list/array traversal, map/priority queue usage, copying, and lots of memory allocation. Currently includes implementations for Java, C, C++, C#, Rust, Go, OCaml, Javascript, and Python. Many more to come - implementing a sliding puzzle solver has become my primary way to learn a new language. 

# Usage
Any puzzle solver executable can be invoked with a command line argument. The command line argument is a path to a file containing newline seperated puzzles to solve.
An example of how valid puzzle files look like are in the files `8puzzles-*.txt` and `15puzzles-*.txt`. Random puzzle file inputs can be generated in `PuzzleGenerator.java` in the java implementation.

An example 3x3 puzzle input looks like so
```
0 1 2
3 4 5
6 7 8
```

A 4x4 like so
```
0 1 2 3
4 5 6 7
8 9 10 11
12 13 14 15
```

A legal puzzle input must contain a 0 representing the empty space, a space between each column, and a newline between rows. Nonzero tiles can be any integers but the program isn't guaranteed to find the shortest path (or any path) nonconventional puzzles. Generally nonzero tiles for a legal puzzle are numbers `1:(N*N-1)`. `N` being the dimension of the puzzle. An 8puzzle would contain integers `1:8` and a 15puzzle integers `1:15` in any order.

# Usage

Build the programs using the Makefile.

```shell
$ make
```

Run the benchmarks using the `run-bench.sh` script.

```shell
$ ./run-bench.sh 8puzzles-small.txt
```

Additionally, you can generate new puzzle inputs using the `./run-generate.sh` script. This is recommended over making your inputs by hand.

```shell
$ ./run-graph.sh
```

# Benchmarks

Machine Specs: AMD Ryzen 7 7700X 8-Core Processor 4.50 GHz, 32 GB RAM

The following results are for the `8puzzles-large.txt` file, containing 1000 3x3 puzzles generated by randomly shifting a solved state 100 times.

| Language   | Ete (ms)   | Total (ms)  | Nodes   | Parallel |
|------------|------------|-------------|---------|----------|
| C          | 10.953     | 160.397     | 727635  | yes      |
| C          | 93.403     | 93.378      | 727635  | no       |
| C++        | 18.12      | 276.21      | 722223  | yes      |
| C++        | 104.92     | 104.89      | 722223  | no       |
| Rust Arena | 10.641     | 158.446     | 705454  | yes      |
| Rust Arena | 87.251     | 86.721      | 705454  | no       |
| Rust Rc    | 17.259     | 259.907     | 705454  | yes      |
| Rust Rc    | 131.861    | 131.344     | 705454  | no       |
| C#         | 85.3341    | 1318.8105   | 751669  | yes      |
| C#         | 242.83     | 242.7177    | 751669  | no       |
| Go         | 51.676     | 795.48      | 737402  | yes      |
| Go         | 251.172    | 251.059     | 737402  | no       |
| Java       | 124.9929   | 1902.9821   | 745730  | yes      |
| Java       | 347.7521   | 346.7364    | 745730  | no       |
| Ocaml      | 1788.023   | 1788.03     | 963634  | no       |
| Nodejs     | 511.6893   | 511.6893    | 717456  | no       |
| Python     | 7814.3025  | 20258.5639  | 717456  | yes      |
| Python     | 10322.0934 | 10268.2252  | 717456  | no       |


These results are for the `15puzzles-large.txt` file, containing 100 4x4 puzzles generated by randomly shifting a solved state 100 times.

| Language   | Ete (ms)   | Total (ms)  | Nodes     | Parallel |
|------------|------------|-------------|-----------|----------|
| C          | 2994.5950  | 13169.640   | 18283069  | yes      |
| C          | 7624.637   | 7624.629    | 18283069  | no       |
| C++        | 7100.01    | 20758.30    | 19189412  | yes      |
| C++        | 13682.83   | 15604.88    | 19189412  | no       |
| Rust Arena | 1996.415   | 6994.175    | 15609985  | yes      |
| Rust Arena | 4513.046   | 4512.973    | 15609985  | no       |
| Rust Rc    | 3304.802   | 12440.968   | 15609985  | yes      |
| Rust Rc    | 9008.035   | 9007.961    | 15609985  | no       |
| C#         | 20466.6375 | 106434.1597 | 20029096  | yes      |
| C#         | 26675.1726 | 26675.0691  | 20029096  | no       |
| Go         | 5221.762   | 22290.145   | 17767899  | yes      |
| Go         | 13165.290  | 13165.260   | 17767899  | no       |
| Java       | 10970.2875 | 44034.4569  | 18769855  | yes      |
| Java       | 25083.6481 | 25082.960   | 18769855  | no       |
| Ocaml      | 91790.277  | 91790.176   | 20769722  | no       | 	
| Nodejs     | 39603.6219 | 39603.6219  | 14601064  | no       |
| Python     | 155136.9342| 679909.7828 | 14601064  | yes      |
| Python     | 437406.3563| 428337.4629 | 14601064  | no       |