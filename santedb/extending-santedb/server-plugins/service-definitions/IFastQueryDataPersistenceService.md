---
description: IFastQueryDataPersistenceService<TEntity> (SanteDB.Core.Api)
---

## Summary
Data persistence service lean mode

## Operations

|Operation|Response/Return|Input/Parameter|Description|
|-|-|-|-|
|QueryFast|IEnumerable&lt;TEntity>|*Expression&lt;Func&lt;TEntity,Boolean>>* **query**<br/>*Guid* **queryId**<br/>*Int32* **offset**<br/>*Nullable&lt;Int32>* **count**<br/>*Int32&* **totalCount**<br/>*IPrincipal* **overrideAuthContext**|Queries or continues a query in lean mode|

## Implementations

None

## Example Implementation
```csharp
/// Example Implementation
using SanteDB.Core.Services;
/// Other usings here
public class MyFastQueryDataPersistenceService<TEntity> : SanteDB.Core.Services.IFastQueryDataPersistenceService<TEntity> { 
	public String ServiceName => "My own IFastQueryDataPersistenceService`1 service";
	/// <summary>
	/// Queries or continues a query in lean mode
	/// </summary>
	public IEnumerable<TEntity> QueryFast(Expression<Func<TEntity,Boolean>> query,Guid queryId,Int32 offset,Nullable<Int32> count,Int32& totalCount,IPrincipal overrideAuthContext){
		throw new System.NotImplementedException();
	}
}
```
