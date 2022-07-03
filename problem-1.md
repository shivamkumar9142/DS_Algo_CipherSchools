=== "C++"

    ```cpp
    #include <bits/stdc++.h>
    
    using namespace std;
    
    class Solution
    {
    public:
        vector<int> nextGreaterElements(vector<int> &nums)
        {
            vector<int> res(nums.size());
            stack<int> st;
            for (int i = 2 * nums.size() - 1; i >= 0; --i)
            {
                while (!st.empty() && nums[st.top()] <= nums[i % nums.size()])
                {
                    st.pop();
                }
                res[i % nums.size()] = st.empty() ? -1 : nums[st.top()];
                st.push(i % nums.size());
            }
            return res;
        }
    };
    
    int main()
    {
        Solution s;
        vector<int> nums = {12, 3, 6, 5, 8, 9, 6, 5, 8};
        s.nextGreaterElements(nums);
        return 0;
    }
    ```

=== "Python"

    ```python
    from io import TextIOWrapper
    from typing import Dict, List
    import os
    
    def write_code(f: TextIOWrapper, filled_num: str, problem_path: str) -> None:
        for extension, lang, tab in [
            ("cpp", "cpp", "C++"),
            ("java", "java", "Java"),
            ("py", "python", "Python"),
        ]:
            code_file_dir = f"{problem_path}/{filled_num}.{extension}"
    
            if not os.path.exists(code_file_dir):
                continue
    
            f.write(f'=== "{tab}"\n\n')
            with open(code_file_dir) as code_file:
                code = ["    " + line for line in code_file.readlines()]
                f.write(f"    ```{lang}\n")
                for line in code:
                    f.write(line)
                f.write("\n")
                f.write("    ```")
                f.write("\n\n")
    
    
    with open("problem-1.md", 'w') as f:
        write_code(f, "main", "./");
    
            
    ```

