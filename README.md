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

#복제 오브젝트
public class Object : MonoBehaviour
{
    
    //게임 오브젝트 생성
    [SerializeField]
    GameObject Prefab;
    private void Awake()
    {
        //오브젝트, 위치, 회전
        Instantiate(Prefab, new Vector3(3, 3, 0), Quaternion.identity);
       
        //회전 각도 설정
        Quaternion quaternion = Quaternion.Euler(0, 0, 45);
        Instantiate(Prefab, new Vector3(3, 3, 0), quaternion);

        //방금 만든 복사본 복제
        GameObject clone = Instantiate(Prefab, Vector3.zero, quaternion);
        //이름변경
        clone.name = "sangchu";
        //색상변경
        clone.GetComponent<SpriteRenderer>().color = Color.yellow;
        //위치변경
        clone.transform.position = new Vector3(3, 3, 0);
        //크기변경
        clone.transform.localScale = new Vector3(0.2f, 0.2f, 0);
    }


    //===================================================
    //배열로 응용
    [SerializeField]
    GameObject[] arrayPrefab;
    private void Update()
    {
        for (int i = 0; i < 30; i++)
        {
            //정수 랜덤 지정(0부터 arrayPrefab배열의 수까지)
            int index = Random.Range(0, arrayPrefab.Length);
            //-7.5부터 7.5까지 정수 
            float x = Random.Range(-7.5f, 7.5f);
            float y = Random.Range(-7.5f, 7.5f);

            Vector3 position = new Vector3(x, y, 0);
            Instantiate(arrayPrefab[index], position, Quaternion.identity);
        }
    }

    //시간 변수
    objectspawntime += Time.deltaTime;
    //0.5초마다 실행
    if(objectspawntime >= 0.5)
}

