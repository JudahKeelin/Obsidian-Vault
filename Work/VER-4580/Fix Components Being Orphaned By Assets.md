
### Current Situation
- Deletion
	- Assets
		- Child assets are deleted alongside their parents
		- Child components are potentially left orphaned as they are not even considered in the code
	- Components
		- Child components are migrated to the grandparent component
		- All components have a parent asset
### Options:
- [ ] A. Both child assets and child components get deleted
- [ ] B. Both child assets and child components migrate to the grandparent
- [ ] C. Child assets get deleted and child components migrate to the nearest ancestor
- [x] D. An option B/C hybrid where users can choose what happens to child assets ✅ 2024-08-22


### Option D Decision Tree

