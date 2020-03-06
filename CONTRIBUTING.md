# Documentation Sprint

## **How to contribute**

1. make a fork of terminusdb/terminus-client and terminusdb/terminus-client-python
2. git clone **your own repo (the one you just forked)**
3. `git remote add upstream <the original terminusdb repo>`
4. claim some functions that you gonna work on in the function list (see below), I would recommend 5-10 functions for today.
    1. assign yourself in the Assignee column
    2. check if the function already have that section
    3. add that section if it is mission (follow the style guide below)
    4. If you have question about how that function work, ask @kevinchekovfeeney or @GavinMendelGleason or @Francesca-Bit (API client)
5. (optional) build the doc page locally to check if you are happy with it (ask @Francesca-Bit for JS and @cheukting for Python)
6. commit your work, write "[Doc] <function you have worked on>" as commit message
7. do a `git pull upstream dev` to make sure your branch is updated
8. push to **your repo**
9. send a pull request to the **dev branch** of terminusdb/terminus-client and terminusdb/terminus-client-python, if you can, put down which function you have worked on in this PR
10. I will review and merge afterwards

[Doc Sprint - WOQL function list](https://www.notion.so/Doc-Sprint-WOQL-function-list-6f0c21910b6b4f48a916e7477683dfb1)

## **Style Guide**

### **Python docstring**

In general, we follow the numpy Docstring Guide: [https://numpydoc.readthedocs.io/en/latest/format.html](https://numpydoc.readthedocs.io/en/latest/format.html) here is complete an example (it may not be correct description, just a style guide example) **Don't use tab in Python, use spaces**:

    def woql_as(self, a=None, b=None, c=None):
            """Imports the value identified by Source to a Target variable

    				When importing columns form a csv, you can use woql_as to assign
            a column to a target variable for data wrangling

            Parameters
            ----------
            a : str
                Source
            b : str
                Target
            c : type
                Type to cast input to

            Returns
            -------
            WOQLQuery object
                query object that can be chained and/or execute

    				Examples
            --------
    				>>> WOQLQuery().get(WOQLQuery().woql_as("Student Name",
            ...                              "v:stu_name",
            ...                              "xsd:string")).\
            ...             remote("http://some_domain.com/some_csv.csv")
            <woqlclient.woql.WOQLQuery object at 0x10dd09278>

            See Also
            --------
            get : import data from CSV
            WOQL.as : WOQL.js version of the same function
            """
            if a is None:
                return

            # the rest of the function

            return self

### JavaScript JSDoc

We will be following the JSDoc here: [https://devhints.io/jsdoc](https://devhints.io/jsdoc), as an example:

    /**
     * Imports the value identified by Source to a Target variable
     * @param {string} map - Source
     * @param {string} vari - Target
     * @return {object} WOQLQuery
     * @example
     * // load Student Name from a csv
     * WOQL.get(WOQL.as("Student Name",
     *                  "v:stu_name",
     *                  "xsd:string"))
     *                  .remote("http://some_domain.com/some_csv.csv");
     * @see {@link get} for import data from CSV
     * @see WOQLQuery().woql_as for WOQL.py version of the same function
     */
    WOQL.as = function(map, vari, ty){	return new WOQLQuery().as(map, vari, ty); }
