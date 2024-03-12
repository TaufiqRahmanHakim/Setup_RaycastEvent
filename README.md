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
    public UnityEvent onHitExit;
    RaycastHit raycastHit;
    private void Update()
    {
        if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out raycastHit, distance))
        {
            onHit.Invoke();
            //Debug.Log("hit something");
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * raycastHit.distance, Color.red);
        }
        else
        {
            onHitExit.Invoke();
            //Debug.Log("Nothing");
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * raycastHit.distance, Color.yellow);
        }
    }
}
```


![fcdnfgjfjryjk](https://github.com/TaufiqRahmanHakim/Setup_RaycastEvent/assets/112629423/1689b3bb-79d7-4976-aab3-1691902da89d)
