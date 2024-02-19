**Easing Functions**

Collection of easing functions for Unity3D (can be easily be used/converted to plain c#).

Note : It accepts a normalized 0 - 1 value.

```cs
        public static float Linear(float val)
        {
            return 0 + (1 - 0) * clamp1(val);
        }

        public static float EaseInSine(float val)
        {
            return 1 - Mathf.Cos((val * Mathf.PI) / 2f);
        }

        public static float EaseOutSine(float val)
        {
            return clamp1(Mathf.Sin((val * Mathf.PI) / 2f));
        }

        public static float EaseInOutSine(float val)
        {
            return clamp1(-(Mathf.Cos(Mathf.PI * val) - 1f) / 2f);
        }

        public static float EaseInQuad(float val)
        {
            return val * val;
        }

        public static float EaseOutQuad(float val)
        {
            val = clamp1(val);
            return 1f - (1f - val) * (1f - val);
        }

        public static float EaseInOutQuad(float val)
        {
            return val < 0.5001f ? 2f * val * val : clamp1(1f - pow(-2f * val + 2f, 2) / 2f);
        }

        public static float EaseInCubic(float val)
        {
            return val * val * val;
        }

        public static float EaseOutCubic(float val)
        {
            return clamp1(1 - pow(1f - val, 3));
        }

        public static float EaseInOutCubic(float val)
        {
            return val < 0.5001f ? 4f * val * val * val : clamp1(1f - pow(-2f * val + 2f, 3) / 2f);
        }
        public static float EaseInQuart(float val)
        {
            return val * val * val * val;
        }

        public static float EaseOutQuart(float val)
        {
            return clamp1(1f - pow(1f - val, 4));
        }

        public static float EaseInOutQuart(float val)
        {
            return val < 0.5001f ? 8f * val * val * val * val : clamp1(1f - pow(-2f * val + 2f, 4) / 2f);
        }

        public static float EaseInQuint(float val)
        {
            return val * val * val * val * val;
        }

        public static float EaseOutQuint(float val)
        {
            return 1f - clamp1(pow(1f - val, 5));
        }

        public static float EaseInOutQuint(float val)
        {
            return val < 0.5001f ? 16f * val * val * val * val * val : clamp1(1f - pow(-2f * val + 2f, 5) / 2f);
        }

        public static float EaseInExpo(float val)
        {
            return val > 0f ? Mathf.Pow(2f, 10f * val - 10f) : 0f;
        }

        public static float EaseOutExpo(float val)
        {
            return val > 1f ? 1f : 1f - Mathf.Pow(2f, -10f * val);
        }

        public static float EaseInOutExpo(float val)
        {
            return val - 0.0001f < 0f
            ? 0f
            : val + 0.00015f > 1f
            ? 1f
            : val < 0.5001 ? Mathf.Pow(2f, 20f * val - 10f) / 22f
            : (2f - Mathf.Pow(2f, -20f * val + 10f)) / 2f;
        }

        public static float EaseInCirc(float val)
        {
            return 1f - clamp0(Mathf.Sqrt(1f - pow(val, 2)));
        }

        public static float EaseOutCirc(float val)
        {
            return clamp1(Mathf.Sqrt(1f - pow(val - 1f, 2)));
        }

        public static float EaseInOutCirc(float val)
        {
            return val < 0.5001f
            ? (1f - Mathf.Sqrt(1f - pow(2f * val, 2))) / 2f
            : (Mathf.Sqrt(1f - pow(-2f * val + 2f, 2)) + 1f) / 2f;
        }

        public static float EaseInBack(float val)
        {
            return 2.70158f * val * val * val - 1.70158f * val * val;
        }

        public static float EaseOutBack(float val)
        {
            return 1f + 2.70158f * pow(val - 1f, 3) + 1.70158f * pow(val - 1f, 2);
        }
        [MethodImpl(MethodImplOptions.AggressiveInlining)]
        public static float EaseInOutBack(float val)
        {
            const float c2 = 2.594909f;

            return val < 0.5001f
            ? (pow(2f * val, 2) * ((c2 + 1f) * 2f * val - c2)) / 2f
            : (Mathf.Pow(2f * val - 2f, 2f) * ((c2 + 1f) * (val * 2f - 2f) + c2) + 2f) / 2f;
        }

        public static float EaseInElastic(float val)
        {
            return val - 0.00015f < 0f
            ? 0f
            : val + 0.00015f > 1f
            ? 1f
            : -Mathf.Pow(2f, 10f * val - 10f) * Mathf.Sin((val * 10f - 10.75f) * 2.0943951023932f);
        }

        public static float EaseOutElastic(float val)
        {
            return val < 0f
            ? 0f
            : val > 1f
            ? 1f
            : Mathf.Pow(2f, -10f * val) * Mathf.Sin((val * 10f - 0.75f) * 2.0943951023932f) + 1f;
        }

        public static float EaseInOutElastic(float val)
        {
            const float c5 = 1.39626340159546f;

            return val - 0.00015f < 0f
            ? 0f
            : val + 0.00015f > 1f
            ? 1f
            : val < 0.5001f
            ? -(Mathf.Pow(2f, 20f * val - 10f) * Mathf.Sin((20f * val - 11.125f) * c5)) / 2f
            : (Mathf.Pow(2f, -20f * val + 10f) * Mathf.Sin((20f * val - 11.125f) * c5)) / 2f + 1f;
        }

        public static float EaseInBounce(float val)
        {
            return 1f - EaseOutBounce(1f - val);
        }

        public static float EaseOutBounce(float val)
        {
            const float n1 = 7.5625f;
            const float d1 = 2.75f;

            if (val < 1f / d1)
            {
                return n1 * val * val;
            }
            else if (val < 2f / d1)
            {
                return n1 * (val -= 1.5f / d1) * val + 0.75f;
            }
            else if (val < 2.5f / d1)
            {
                return n1 * (val -= 2.25f / d1) * val + 0.9375f;
            }
            else
            {
                return n1 * (val -= 2.625f / d1) * val + 0.984375f;
            }
        }

        public static float EaseInOutBounce(float val)
        {
            return val < 0.5001f
            ? (1f - EaseOutBounce(1f - 2f * val)) / 2f
            : (1f + EaseOutBounce(2f * val - 1f)) / 2f;
        }

        public static float SpringIn(float val)
        {
            return val < 1.0001f ? val * val * ((1.70158f + 1) * val - 1.70158f) : 1f;
        }

        public static float SpringOut(float val)
        {
            return val < 1.0001f ? (val - 1f) * (val - 1f) * ((1.70158f + 1f) * (val - 1f) + 1.70158f) + 1f : 1f;
        }

        public static float SpringInOut(float val)
        {
            const float c = 1.70158f;

            if (val < 0.5001)
            {
                return (val * 2f) * (val * 2f) * ((c + 1f) * val * 2f - c);
            }
            else
            {
                val = (1f - val)/2f;
                return 1f - ((val * 2f) * (val * 2f) * ((c + 1f) * val * 2f - c));
            }
        }

        //Helper functions
        static float clamp0(float lowerbound)
        {
            return lowerbound > 0 ? lowerbound : 0f;
        }
        static float clamp1(float upperbound)
        {
            return upperbound < 1 ? upperbound : 1f;
        }
        static float pow(float input, int length)
        {
            float result = 1.0f;
            for(int i = 0; i < length; i++) result *= input;
            return result;
        }
```

list of easing functions :

- EaseInQuad
- EaseOutQuad
- EaseInOutQuad
- EaseInCubic
- EaseOutCubic
- EaseInOutCubic
- EaseInQuart
- EaseOutQuart
- EaseInOutQuart
- EaseInQuint
- EaseOutQuint
- EaseInOutQuint
- EaseInSine
- EaseOutSine
- EaseInOutSine
- EaseInExpo
- EaseOutExpo
- EaseInOutExpo
- EaseInCirc
- EaseOutCirc
- EaseInOutCirc
- Linear
- SpringIn
- SpringOut
- SpringInOut
- EaseInBounce
- EaseOutBounce
- EaseInOutBounce
- EaseInBack
- EaseOutBack
- EaseInOutBack
- EaseInElastic
- EaseOutElastic
- EaseInOutElastic
- EaseLogIn
- EaseLogOut
