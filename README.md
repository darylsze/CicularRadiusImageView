# CicularRadiusImageView

Code example for people who are seeking for circular or radius-support imageview


Simple usage:
1. Copy file into your project
2. Use it in your xml layout, replace imageview with this circular image view
3. (optional) if you want to set radius and border type (say, circular or radius),
in your code you may follow this:

```kotlin
override fun onBindViewHolder(holder: ListingRvVerticalCellVH, position: Int) {
        val isOdd = position % 2 != 0
        if (isOdd) {
            // for odd item, icon shows circular
            holder.view.imgAppIcon.borderType = BorderType.Circular
        } else {
            // for even item, icon shows 20f radius
            holder.view.imgAppIcon.borderType = BorderType.Radius
            holder.view.imgAppIcon.radius = 20f
        }
        holder.onBindView(holder.itemView, dataset[position])
    }
```

This is a simple implementation demo usage in recyclerview.
