# unity-basic
public class Bechu : MonoBehaviour
{
    
    //속도 선언
    [SerializeField]//유니티에서 바꿀수 있게 도와줌
    float speed;
    //방향 선언
    Vector3 vector = Vector3.zero;
    [SerializeField]
    public GameObject bullet;
    [SerializeField]
    KeyCode firekey = KeyCode.Space;
    Vector3 initialdirection = Vector3.right;


    private void Update()
    {
        float x = Input.GetAxisRaw("Horizontal");
        float y = Input.GetAxisRaw("Vertical");
        vector = new Vector3(x, y, 0);
        transform.position += vector * speed * Time.deltaTime;
        
        }

    }
