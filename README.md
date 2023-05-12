# unity-basic
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
 
 




