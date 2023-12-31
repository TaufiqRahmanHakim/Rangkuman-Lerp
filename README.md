# Rangkuman-Lerp
Rangkuman Lerp di unity

# Learning Lerp in Unity C#

## Table of Contents

1. [Lerp](#lerp)
2. [Vector3 Lerp](#vector3-lerp)
3. [Time.deltaTime](#timedeltaTime)
4. [Coroutines](#coroutines)
5. [Mathf.Clamp / Mathf.Clamp01](#mathfclamp--mathfclamp01)
6. [Mathf.SmoothStep](#mathfsmoothstep)
7. [Quaternion.Lerp / Quaternion.Slerp](#quaternionlerp--quaternionslerp)
8. [Inverse Lerp](#inverse-lerp)
9. [Easing Functions](#easing-functions)
10. [DeltaTime vs FixedDeltaTime](#deltatime-vs-fixeddeltatime)
11. [Rigidbody Interpolation](#rigidbody-interpolation)
12. [Vector2 Lerp](#vector2-lerp)
13. [Color Lerp](#color-lerp)
14. [Animation Curves](#animation-curves)
15. [LateUpdate](#lateupdate)
16. [Transform Lerp](#transform-lerp)
17. [Debugging Tools](#debugging-tools)
18. [Variables](#variables)

---

### Lerp

Linear interpolation between two values.

```csharp
float hasil = Mathf.Lerp(0f, 10f, 0.5f);
```

---

### Vector3 Lerp

Lerp for Vector3 objects, commonly used for position.

```csharp
Vector3 posisi = Vector3.Lerp(Vector3.zero, new Vector3(10, 10, 10), 0.5f);
```

---

### Time.deltaTime

For smoother interpolation over time.

```csharp
float t = 0.5f * Time.deltaTime;
```

---

### Coroutines

Interpolation based on actual time using Coroutines.

```csharp
IEnumerator DoLerp() {
    float t = 0;
    while (t < 1) {
        t += Time.deltaTime;
        transform.position = Vector3.Lerp(Vector3.zero, new Vector3(10, 10, 10), t);
        yield return null;
    }
}
```

---

### Mathf.Clamp / Mathf.Clamp01

Limits the interpolation value between 0 and 1.

```csharp
float t = Mathf.Clamp01(1.2f);
```

---

### Mathf.SmoothStep

A smoother version of Lerp.

```csharp
float hasil = Mathf.SmoothStep(0f, 10f, 0.5f);
```

---

### Quaternion.Lerp / Quaternion.Slerp

For interpolating rotations.

```csharp
Quaternion rotasi = Quaternion.Lerp(Quaternion.identity, Quaternion.Euler(0, 90, 0), 0.5f);
```

---

### Inverse Lerp

Finds the `t` parameter that would result in a given value in a Lerp operation.

```csharp
float t = Mathf.InverseLerp(0f, 10f, 5f);
```

---

### Easing Functions

Modify `t` for more natural motion effects.

```csharp
float EaseInQuad(float t) {
    return t * t;
}
```

---

### DeltaTime vs FixedDeltaTime

Understanding the difference between time updates.

```csharp
// In Update()
float t = 0.5f * Time.deltaTime;

// In FixedUpdate()
float t = 0.5f * Time.fixedDeltaTime;
```

---

### Rigidbody Interpolation

Settings in Rigidbody component for interpolation.

```csharp
// This is set in the Unity Editor, not in code
myRigidbody.interpolation = RigidbodyInterpolation.Interpolate;
```

---

### Vector2 Lerp

Lerp for 2D objects.

```csharp
Vector2 posisi = Vector2.Lerp(Vector2.zero, new Vector2(10, 10), 0.5f);
```

---

### Color Lerp

Interpolating between colors.

```csharp
Color warna = Color.Lerp(Color.red, Color.blue, 0.5f);
```

---

### Animation Curves

For more control over how an object interpolates over time.

```csharp
// This is set in the Unity Editor, not in code
public AnimationCurve myCurve;
```

---

### LateUpdate

An alternative place for doing Lerp operations.

```csharp
void LateUpdate() {
    // Your Lerp code here
}
```

---

### Transform Lerp

Interpolating the scale of an object.

```csharp
transform.localScale = Vector3.Lerp(new Vector3(1, 1, 1), new Vector3(2, 2, 2), 0.5f);
```

---

### Debugging Tools

Debugging tools to understand what's happening.

```csharp
Debug.Log("Nilai t adalah: " + t);
Debug.DrawLine(Vector3.zero, new Vector3(10, 10, 10), Color.red);
```

---

### Variables

1. **t**: Faktor interpolasi, biasanya antara 0 dan 1. Jika t = 0, hasilnya adalah titik awal. Jika t = 1, hasilnya adalah titik akhir.
    ```csharp
    float t = 0.5f;
    ```

2. **startValue**: Nilai awal yang ingin di-interpolasi.
    ```csharp
    float startValue = 0f;
    ```

3. **endValue**: Nilai akhir yang ingin di-interpolasi.
    ```csharp
    float endValue = 10f;
    ```

4. **result**: Hasil dari operasi `Lerp`.
    ```csharp
    float result = Mathf.Lerp(startValue, endValue, t);
    ```

5. **speed**: Kecepatan interpolasi, biasanya digunakan bersama dengan `Time.deltaTime`.
    ```csharp
    float speed = 2f;
    ```

6. **deltaTime**: Selisih waktu antara frame, digunakan untuk interpolasi yang smooth.
    ```csharp
    float deltaTime = Time.deltaTime;
    ```

7. **clamp**: Pembatasan nilai `t`, biasanya menggunakan `Mathf.Clamp` atau `Mathf.Clamp01`.
    ```csharp
    float clamp = Mathf.Clamp01(t);
    ```

8. **lerpTime**: Waktu yang diperlukan untuk menyelesaikan proses interpolasi dari awal hingga akhir.
    ```csharp
    float lerpTime = 3.0f;
    ```

9. **currentTime**: Waktu saat ini dalam proses interpolasi, sering digunakan di Coroutines.
    ```csharp
    float currentTime = 0f;
    ```

10. **easingFunction**: Fungsi penyesuaian `t` untuk efek lebih natural.
    ```csharp
    float EaseInQuad(float t) { return t * t; }
    ```

11. **direction**: Arah vektor, sering digunakan dalam interpolasi posisi.
    ```csharp
    Vector3 direction = targetPosition - startPosition;
    ```

12. **step**: Ukuran langkah per frame, biasanya `speed * Time.deltaTime`.
    ```csharp
    float step = speed * Time.deltaTime;
    ```
