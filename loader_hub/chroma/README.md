# Chroma Loader

The Chroma Loader returns a set of texts corresponding to embeddings retrieved from a Chroma Index.
The user initializes the loader with a Qdrant index. They then pass in a query vector.

## Usage

Here's an example usage of the ChromaReader.

```python
from llama_index.readers.chroma import ChromaReader
from llama_index.indices import GPTListIndex

# The chroma reader loads data from a persisted Chroma collection.
# This requires a collection name and a persist directory.
reader = ChromaReader(
    collection_name="chroma_collection",
    persist_directory="examples/data_connectors/chroma_collection"
)

query_vector=[n1, n2, n3, ...]

documents = reader.load_data(collection_name="demo", query_vector=query_vector, limit=5)
index = GPTListIndex(documents)

response = index.query("<query_text>")
display(Markdown(f"<b>{response}</b>"))
```

This loader is designed to be used as a way to load data into [LlamaIndex](https://github.com/jerryjliu/gpt_index/tree/main/gpt_index) and/or subsequently used as a Tool in a [LangChain](https://github.com/hwchase17/langchain) Agent. See [here](https://github.com/emptycrown/llama-hub/tree/main) for examples.
