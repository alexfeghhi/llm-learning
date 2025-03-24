# Notes

### **Build LLM from Scratch(BLLMFS)**
**(Chapter 2: Working with Text Data)**
  - This chapter covers processing steps to be done with raw text data before use in an LLM
  - Since raw text cannot be used as input, a key step is tokenization
    - Tokenization involves splitting text into tokens(tokens are kinda like words) and mapping tokens to numbers
    - All the tokens combined are the vocab of the llm
    - Some potential issues include unknown words:
      - There are special tokens to handle this and other issues:
      - UNK tokens represent unknown words, padding tokens pad sequences to the batch size, and there are special tokens to denote the end of a passage/seperate passages from eachother
    - You could regex this but apparently SOTA llms use Byte-pair encoding. The details of this are not covered in the text but I will explore and implement this
    - There is a step after tokenization where the tokens are embedded
      - I think this means shifting it into a high-dimensional space using matrix multiplcation
      - I guess this makes sense and DL algorithms like big dimensions over small ones(tokens are 1d)
      - Embeddings vary based on task obviously
      - Embeddings can be trained as well apparently
      - Relative and absolute embeddings help encode positional data
  - Other data preprocessing
    - Stride
      - We take the dataset and shift by one so that slicing both allows us to easy get input and predication pairs
    - Context size
      - max number of tokens in each training example
    - Batch size
      - number of training examples at once

### Thoughts
- BLLMFS:
  - There are three different areas I want to focus on in depth
    - Tokenization
      - I want to understand the tokenization methods used, especially whatever SOTA is(I think its byte pair encoding)
    - Embedding
      - I think getting a good intuition on this is also important
    - Other dataset related stuff
      - I am curious as to how massive datasets are handled
      - Also curious about hyperparameters: the book mentions stride and max_length


### Exploring topics in depth
- Tokenization:
  - There are differnet methods that split into different sizes of tokens: characters, subwords, and words
    - The tradeoffs and implications of this are unclear, at least as I do not fully understand the transformer architecture
- Embeddings:
  -

### Projects

- **Sample code from BLLMFS chapter**
  - Code includes downloading a dataset,regex tokenization, slicing/loading, and embeddings
  
- **Byte-Pair Encoding Implementation**
  - Build BPE tokenizer from scratch
  - Compare with regex-based tokenization
  - Test on sample texts

- **Embedding Experiments**
  - Create basic token embeddings
  - Implement positional encodings
  - Visualize token representations

- **Data Loading & Batching**
  - Build efficient data loader
  - Implement striding mechanism
  - Handle variable sequence lengths
