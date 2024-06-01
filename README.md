# lab-mandaroty10

## Provided Code Snippets:
### JavaScript Snippet:

```
// Inefficient loop handling and excessive DOM manipulation
function updateList(items) {
  let list = document.getElementById("itemList");
  list.innerHTML = "";
  for (let i = 0; i < items.length; i++) {
    let listItem = document.createElement("li");
    listItem.innerHTML = items[i];
    list.appendChild(listItem);
  }
}
```
* **Code Analysis:** The problem in this case is that the for iteration is refreshing the page every time, so the solution is to take the refresh out of the loop
* **Implementing Optimizations:**
```
// Inefficient loop handling and excessive DOM manipulation
function updateList(items) {
  let list = document.getElementById("itemList");
  const fragment = document.createDocumentFragment();
  for (let i = 0; i < items.length; i++) {
    const listItem = document.createElement("li");
    listItem.innerHTML =  items[i];
    fragment.appendChild(listItem);
  }
  document.body.appendChild(fragment);
}
```

### Java Snippet:

```
// Redundant database queries
public class ProductLoader {
    public List<Product> loadProducts() {
        List<Product> products = new ArrayList<>();
        for (int id = 1; id <= 100; id++) {
            products.add(database.getProductById(id));
        }
        return products;
    }
}
```
* **Code Analysis:** Here we can remove the for and retrieve products 1 to 100 with a single query
* **Implementing Optimizations:**
```
public class ProductLoader {
    public List<Product> loadProducts() {
        List<Product> products = new ArrayList<>();
        List<Integer> ids = IntStream.rangeClosed(1,100).boxed().toList();
        return products.add(database.getProductByIdsIn(ids));
    }
}
```

### C# Snippet:

```
// Unnecessary computations in data processing
public List<int> ProcessData(List<int> data) {
    List<int> result = new List<int>();
    foreach (var d in data) {
        if (d % 2 == 0) {
            result.Add(d * 2);
        } else {
            result.Add(d * 3);
        }
    }
    return result;
}
```
* **Code Analysis:** Using LINQ to simplify and optimize processing
* **Implementing Optimizations:**
```
public List<int> ProcessData(List<int> data) {
  return data.Select(d => d % 2 == 0 ? d * 2 : d * 3).ToList();
}
```

