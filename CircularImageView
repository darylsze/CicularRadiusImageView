import android.content.Context
import android.graphics.*
import android.graphics.drawable.BitmapDrawable
import android.graphics.drawable.Drawable
import android.util.AttributeSet
import android.widget.ImageView


/**
 * Created by darylsze on 8/2/2018.
 */

enum class BorderType {
    Radius, Circular
}

class CircularImageView @JvmOverloads constructor(
    context: Context,
    attrs: AttributeSet? = null,
    style: Int = 0
) : ImageView(context, attrs, style) {

    val paint by lazy { Paint().apply { isAntiAlias = true } }
    var borderType: BorderType = BorderType.Circular
    var radius: Float = 15f

    override fun onDraw(canvas: Canvas) {
        val bitmap = loadBitmap() ?: return

        val shader = BitmapShader(Bitmap.createScaledBitmap(bitmap, canvas.width, canvas.height, false), Shader.TileMode.CLAMP, Shader.TileMode.CLAMP)
        paint.shader = shader

        when (borderType) {
            BorderType.Circular -> {
                val circleCenter = measuredWidth / 2
                canvas.drawCircle(circleCenter.toFloat(), circleCenter.toFloat(), circleCenter - 4.0f, paint)
            }
            BorderType.Radius -> {
                val bitmapRect = RectF().apply {
                    set(0f, 0f, measuredWidth.toFloat(), measuredWidth.toFloat())
                }
                canvas.drawRoundRect(bitmapRect, radius, radius, paint)
            }
        }

    }

    override fun onMeasure(widthMeasureSpec: Int, heightMeasureSpec: Int) {
        val height = MeasureSpec.getSize(heightMeasureSpec)
        val width = MeasureSpec.getSize(widthMeasureSpec)

        setMeasuredDimension(width, height)
    }

    private fun loadBitmap(): Bitmap? {
        return (drawable as? BitmapDrawable)?.bitmap
    }
}
