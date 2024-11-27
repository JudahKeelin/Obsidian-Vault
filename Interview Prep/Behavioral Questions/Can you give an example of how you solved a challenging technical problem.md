
## **Cascading Asset Deletion Story**
##### **Situation:**  
In our app, users can create assets and organize them into a hierarchical tree structure. However, there was no way to delete an entire branch of the tree—users had to delete each asset manually. As the company grew, so did our clients, with some managing thousands of assets. This made the deletion process inefficient and time-consuming.
##### **Task:**  
I was tasked with creating a feature to allow users to delete entire branches of the asset tree in one action.
##### **Action:**  
I began by collaborating with the Subject Matter Expert (SME) to fully understand the requirements and potential side effects of deleting assets. During these discussions, we identified a significant challenge: our app also had a secondary "component" tree. Components could have both a parent component and a parent asset. If a parent component was deleted but not its parent asset, the component could become orphaned in the component tree.

To address this, I implemented a depth-first search to gather a list of all child assets and components within the branch targeted for deletion. I then iterated through this list, migrating child assets and components to their nearest available parent node—either in the asset or component tree—before deleting the original node. This ensured the integrity of both trees while preventing orphaned nodes. This approach also allowed for clearer logging, making erroneous deletions easier to identify and reverse.

I also accounted for an edge case where the origin node of the branch being deleted was a top-level asset in the tree. If this asset were deleted, there would be no parent node for child assets and components to migrate to. After consulting with the SMEs, I implemented a safeguard to prevent cascade deletion in this scenario and added a danger message explaining the reasoning to the user.
##### **Result:**  
The final solution met all design requirements and significantly improved usability for large clients. Users could now efficiently manage and delete entire branches of their asset hierarchy, saving time and reducing errors in large-scale operations.