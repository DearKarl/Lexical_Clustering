# Lexical Clustering in Narrative Texts

Lexical distance modelling and Dijkstra‑refined clustering on Project Gutenberg texts

## Project Overview  

This repository presents a natural language processing workflow for unsupervised lexical clustering in narrative texts. The pipeline begins with text cleaning and preprocessing of novels from Project Gutenberg to obtain a consistent corpus. A balanced vocabulary of 100 words is then constructed through synonym de-duplication, ensuring semantic diversity while reducing redundancy. Pairwise lexical relationships are modelled using both global token distributions and sentence-level co-occurrence, capturing long-range and local semantic dependencies. To address data sparsity, a graph-based representation is employed and refined via Dijkstra’s shortest-path algorithm, which integrates indirect connections between words. Finally, clustering is applied to the resulting embeddings, with quantitative evaluation metrics and visualisation used to assess the quality of the discovered word groups. The project thus combines classical graph algorithms with modern NLP-driven representation learning, providing a machine learning framework for semantic structure discovery in narrative text corpora.

## Background  

Textual corpora such as novels contain rich lexical and syntactic patterns that can reveal how words relate to one another beyond simple frequency counts. Traditional word co-occurrence analyses often rely on direct adjacency or statistical embeddings, but these methods can obscure the underlying structural patterns of how words are distributed across long narratives. By focusing on positional information — how far apart words occur globally across a corpus, or how close they appear locally within the same sentence — we can capture different layers of linguistic association. This enables a more interpretable and linguistically motivated view of lexical similarity.  

However, sentence-local distances introduce sparsity: many semantically related words never co-occur directly in a single sentence, resulting in artificially large or disconnected distances. To address this, we refine distances with a graph-based approach, applying Dijkstra’s shortest paths to uncover indirect lexical links. By comparing clustering results from raw positional distances versus graph-refined distances, this project evaluates how structural proximity and indirect connections shape the organisation of words in narrative texts. This dual perspective highlights both the limitations of local co-occurrence and the potential of graph methods for enriching lexical analysis.  

## Project Goal  

Unsupervised clustering of a curated **~100-word vocabulary (L)** from narrative text using **positional distance metrics**, then **graph-based refinement with Dijkstra’s shortest paths** to mitigate sparsity and re-evaluate clustering structure.

## Methods Overview  

We first developed a unified corpus from Project Gutenberg novels by removing non-narrative content such as boilerplate, chapter headers, and appendices. Sentences were segmented with spaCy, and linguistic filtering ensured sufficient syntactic richness. Named entities and frequent multi-word expressions were merged, and tokens were lemmatised with part-of-speech (POS) tags preserved. From this processed corpus, we constructed a representative 100-word vocabulary balanced across nouns, verbs, adjectives, and adverbs, while synonym de-duplication maintained semantic diversity.  

To measure lexical relationships, we modelled pairwise distances using both global token-level separation and sentence-local co-occurrence. As sparse sentence-local distances often yielded disconnected pairs, we constructed a lexical graph and applied Dijkstra’s shortest paths to infer indirect proximities. Hierarchical clustering with multiple linkage strategies was then applied to both raw and Dijkstra-refined distances, and results were evaluated with multidimensional scaling (MDS) visualisations and silhouette scores to assess clustering quality.  

## Highlights  
- Construction of a cleaned and linguistically enriched corpus from Project Gutenberg novels for reliable lexical analysis  
- Development of complementary distance measures and a graph-based refinement with Dijkstra’s algorithm to address sparsity in co-occurrence data  
- Comprehensive clustering evaluation with hierarchical methods, multidimensional scaling, silhouette scoring, and linguistic interpretation of results  

## Data Sources  

- [Project Gutenberg](https://www.gutenberg.org/)  

All narrative texts analysed in this project were downloaded from **Project Gutenberg**, a public-domain digital library. 

## References
- Levy, O. & Goldberg, Y. *et al.* (2014). *Neural word embedding as implicit matrix factorisation.* NeurIPS.  
- Navigli, R. & Lapata, M. *et al.* (2007). *Graph connectivity measures for unsupervised word sense disambiguation.* ACL.  
- Boytsov, L. *et al.* (2015). *Alternative architectures for Dijkstra’s algorithm in large graphs.* Proc. ACM SIGIR.  
- Veremyev, A. *et al.* (2019). *Graph-based models for semantic relatedness.* J. Complex Networks.  

---

> Repository maintained by [DearKarl](https://github.com/DearKarl). Contributions and feedback welcome.
