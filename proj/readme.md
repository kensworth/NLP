Oftentimes people non-versed in database languages need to access data. Although languages like SQL are relatively simple to learn, formulating a query with the correct syntax can be tedious and error prone. Therefore, I believe it would be a very useful tool to be able to convert human speech into SQL or other relational database queries. The goal of this project is to be able to allow anyone with a basic idea of what information exists in a database to execute queries on that database with nothing more than natural language.

For this project I will be using NLTK's tokenizer and taking inspiration from the theoretical paper 'Natural Language Statement to SQL Query Translator' by MIT's Pranali Chaudhari. The algorithm involves a preprocessing stage, where the query type is parsed and all relevant parameters extracted, and a postprocessing stage, where the parameters are matched to table values, grouped properly, and turned into a query. The system will be written in Python and will be tested on an actaul MySQL database for an online forum. 

A simple representation of how that might look is:
sentence -> type of query -> replace numerals -> substitute comparison operator -> remove apostrophes -> extract noun phrase

Potential difficulties of this project are: making sure different variations of the same sentence parse into the same query, and differentiating sentences that are syntactically similar but different in meaning. I believe one way to reduce some error is to introduce the idea of templating, where sentences are broken down and different words are modified and put into existing SQL command templates. A template might look something like: [query type] (ex. 'select' or 'delete') [column query] (ex. 'ID') [table name] (ex. 'from students') [query clause] (ex. 'where firstName = "John"'). For example, after putting the sentence through NLTK's word_tokenize, we could deduce the type of query by looking at if a verb phrase exists or not. A sentence like 'find me John's ID number' would label 'find' as the verb. Through a lookup table we could have 'find' mapped to the SQL command 'select,' 'John' as the subject of the query clause due to "John's" being labed as an NNS, and so on. 

The potential impact to industry a well functioning natural language to SQL converter could have is vast, and I think this project would be an interesting attempt to birth such an idea into existence. Currently I, Kenneth Zhang, am working alone on this project, but that may be subject to change in the near future.