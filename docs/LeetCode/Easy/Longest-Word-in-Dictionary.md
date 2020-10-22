## [Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary)

<p>Given a list of strings <code>words</code> representing an English Dictionary, find the longest word in <code>words</code> that can be built one character at a time by other words in <code>words</code>.  If there is more than one possible answer, return the longest word with the smallest lexicographical order.</p>  If there is no answer, return the empty string.

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> 
words = ["w","wo","wor","worl", "world"]
<b>Output:</b> "world"
<b>Explanation:</b> 
The word "world" can be built one character at a time by "w", "wo", "wor", and "worl".
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> 
words = ["a", "banana", "app", "appl", "ap", "apply", "apple"]
<b>Output:</b> "apple"
<b>Explanation:</b> 
Both "apply" and "apple" can be built from other words in the dictionary. However, "apple" is lexicographically smaller than "apply".
</pre>
</p>

<p><b>Note:</b>
<li>All the strings in the input will only contain lowercase letters.</li>
<li>The length of <code>words</code> will be in the range <code>[1, 1000]</code>.</li>
<li>The length of <code>words[i]</code> will be in the range <code>[1, 30]</code>.</li>
</p>

## Solutions
#### 🧠 Cpp
```cpp
#define all(x) begin(x),end(x)

class Solution
{
    
    struct TrieNode
    {
        char value = ' ';
        bool is_wordend = false;
        vector<shared_ptr<TrieNode>> nodes;
    };
    
    shared_ptr<TrieNode> createTrie(const vector<string>& words)
    {
        auto root = make_shared<TrieNode>();
        
        //translate vector of strings into trie
        for(const auto &str : words)
        {
            //start inserting new word from trie root
            auto trie_pointer = root;
            for(auto ch_iter = begin(str); ch_iter < end(str); ++ch_iter)
            {
                const char ch = *ch_iter;
                const bool char_present_in_trie = std::any_of(all(trie_pointer->nodes),
                    [&trie_pointer, ch](auto node)
                    {
                      bool found = node->value == ch;
                      if (found)
                          trie_pointer = node;
                        return found;
                    });
                
                //insert new node
                if(!char_present_in_trie)
                {
                    auto node = make_shared<TrieNode>();
                    node->value = ch;
                    trie_pointer->nodes.push_back(node);
                    trie_pointer = node;
                }
                
                if(ch_iter == prev(end(str)))
                    trie_pointer->is_wordend = true;
            }
        }
        
        return root;
    }
public:
    
    vector<string> get_words_formed_by_words(const shared_ptr<TrieNode> root)
    {
        vector<string> res;
        
        for(auto &leaf : root->nodes)
        {
            if(leaf->is_wordend)
            {
                res.emplace_back(1, leaf->value);
            
                vector<string> subres = get_words_formed_by_words(leaf);
                if(!subres.empty())
                {
                    string last_letter = res.back();
                    for(auto &str : subres)
                    res.push_back(last_letter + str);
                }
            }
        }
        
        return res;
    }
    
    string longestWord(vector<string>& words)
    {
        //O(n)
        auto root = createTrie(words);
        
        //O(n)
        vector<string> wfbw = get_words_formed_by_words(root);
        
        //O(n)
        return *max_element(all(wfbw), 
                            [](auto a, auto b)
                            {
                                return a.size() == b.size() ?
                                       a > b :
                                       a.size() <  b.size();
                            });
    }
};
```
