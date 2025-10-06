
* Sparse vs Dense:

**OneHotEncoder** outputs a **sparse matrix** by default → memory efficient if many categories.

Use **.toarray()** to convert it into a dense NumPy array → easier to wrap in pandas.DataFrame



---


- Convert categorical columns ('store_and_fwd_flag', 'vendor_id') into numeric binary format.
    - 'store_and_fwd_flag': Y -> 1, N -> 0
    - 'vendor_id': 2 -> 1, 1 -> 0 
    - This helps the model understand these features numerically.\
```python

train["store_and_fwd_flag"] = (train["store_and_fwd_flag"] == "Y").astype(int)
train["vendor_id"] = (train["vendor_id"] == 2).astype(int)

val["store_and_fwd_flag"] = (val["store_and_fwd_flag"] == "Y").astype(int)
val["vendor_id"] = (val["vendor_id"] == 2).astype(int)

test["store_and_fwd_flag"] = (test["store_and_fwd_flag"] == "Y").astype(int)
test["vendor_id"] = (test["vendor_id"] == 2).astype(int)

```
---


`pd.cut()` is a **pandas function** that takes a numerical **Series** (or array-like input) and divides its continuous values into **discrete categorical intervals (bins)**.

**Syntax:**

```python
pd.cut(x, bins, labels=None, right=True, include_lowest=False)
```

* `x`: the Series to be binned (e.g., `df["avg_speed_proxy"]`).
* `bins`: the numeric boundaries defining each interval.
* `labels`: optional labels or category names for each bin.

Example:

```python
pd.cut(df["avg_speed_proxy"],
       bins=[-1, 0.5, 1.5, 3, np.inf],
       labels=[3, 2, 1, 0])
```

This converts a continuous speed column into traffic-level categories:

* `<0.5` → heavy traffic (3)
* `0.5–1.5` → moderate traffic (2)
* `1.5–3` → light traffic (1)
* `>3` → no traffic (0)

The result is a **categorical Series** that makes patterns easier for the model to interpret.
