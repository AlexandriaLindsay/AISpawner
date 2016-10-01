
public class EnemySpawner:MonoBehaviour{

	public float Speed ;
	public Transform spawnLeft;
	public Transform spawnRight;

	public List <GameObject> toSpawn = new List <GameObject> ();

// Use this for initialization
void Start () {
	InvokeRepeating ("spawnIt", 2, 4);
	
}
public void spawnIt()
{ 
	Vector3 randomPos = Vector3.Lerp (spawnLeft.position, spawnRight.position,
	                                  Random.Range (0,100) * 0.03f);
	
		int roll = Random.Range (0, toSpawn.Count);
		//Debeg.LogError("ROLL IS " + roll);
		GameObject prefab = toSpawn [roll];

	GameObject.Instantiate (prefab, randomPos, Quaternion.identity);
}

// Update is called once per frame
void Update () {
	transform.position = Vector3.MoveTowards(transform.position, spawnLeft.position, Speed);
		transform.position += transform.right * Speed * Time.deltaTime;
	
}
}
