# Setup_RaycastEvent
RaycastEvent is component for easy setup raycast

# Source Code
```csharp
using UnityEngine;
using UnityEngine.Events;

public class RaycastEvent : MonoBehaviour
{
    [SerializeField] private float distance;

    public UnityEvent onHit;
    public UnityEvent onHitOnce;
    public UnityEvent onHitOnceEveryHit;
    public UnityEvent onHitOnceExit;
    public UnityEvent onHitExit;

    RaycastHit raycastHit;
    private bool hasHitOnce = false;
    private bool hasHitOnceEveryHit = false;
    private bool hasHitOnceExit = false;

    private void Update()
    {
        if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out raycastHit, distance))
        {
            if (!hasHitOnceEveryHit) 
            {
                if (!hasHitOnce)
                {
                    onHitOnce.Invoke();
                    hasHitOnce = true;
                }
                onHitOnceEveryHit.Invoke();
                hasHitOnceEveryHit = true;
                hasHitOnceExit = false;
            }
            onHit.Invoke();
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * raycastHit.distance, Color.red);
        }
        else
        {
            if (!hasHitOnceExit)
            {
                onHitOnceExit.Invoke();
                hasHitOnceExit = true;

            }
            onHitExit.Invoke();
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * raycastHit.distance, Color.yellow);
            hasHitOnceEveryHit = false;
        }
    }
    public void debugRayOnHit() => Debug.Log("debugRayOnHit");
    public void debugRayOnce() => Debug.Log("debugRayOnce");
    public void debugRayOnceEveryHit() => Debug.Log("debugRayOnceEveryHit");
    public void debugRayOnceExit() => Debug.Log("debugRayOnceExit");
    public void debugRayOnExit() => Debug.Log("debugRayOnExit");
}

```
# preview component
![iughiughkih](https://github.com/TaufiqRahmanHakim/Setup_RaycastEvent/assets/112629423/f8af7c43-3dd7-420a-8b20-5bc1512ae305)


# preview

https://github.com/TaufiqRahmanHakim/Setup_RaycastEvent/assets/112629423/d2555b3b-e461-4488-bad7-44b67e99b2d3

