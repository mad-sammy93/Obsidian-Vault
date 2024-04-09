1) Could we include the **total number of items** in the query as this is required to set table pagination and is different from **pageLimit**
2) status value in request change from **ACTIVE** to numbers
3) page, rowsPerPage, **sortBy, sortType** separating *SortBy* and *sort type*
4) One more thing, I would like the **access token** to have a parameter called **isAdmin**
5)   
   "company": { 
	"id": 2,  
		"**name**": "Smartshoreability"  
	},  
	{
		"project": {  
		"**title**": "Devops Dashboard"  
	} ```
both should have key as name

6) Currently the user listing asks for sort parameters with options'name', 'project', 'company', 'createdAt'
- but the response is userProjects 
