# unity-basic
#이동
public class Bechu : MonoBehaviour
{
    
    //속도 선언
    [SerializeField]//유니티에서 바꿀수 있게 도와줌
    float speed;
    //방향 선언(방향 제로)
    Vector3 vector = Vector3.zero;
    Vector3 initialdirection = Vector3.right;


    private void Update()
    {
        float x = Input.GetAxisRaw("Horizontal");
        float y = Input.GetAxisRaw("Vertical");
        //방향 새로 대입해짐
        vector = new Vector3(x, y, 0);
        transform.position += vector * speed * Time.deltaTime;
        
        }

    }
    
 }
 
 #충돌과 색깔
 public class Collider : MonoBehaviour
{
    
    
    //색깔 선언
    [SerializeField]
    Color color;
    //이 컴포넌트가 있는 오브젝트 = spriteRenderer
    SpriteRenderer spriteRenderer;
    private void Awake()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
    }
    //부딫친순간
    private void OnCollisionEnter2D(Collision2D collision)
    {
        //선언한 색깔 바꾸기
        spriteRenderer.color = color;
    }
    //부딪친곳에서 벗어난순간
    private void OnCollisionExit2D(Collision2D collision)
    {
        //하얀색으로 바꾸기
        spriteRenderer.color = Color.white;
    }
}
