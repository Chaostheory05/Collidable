# Collidable
// This code is from Epitome's tutorial https://www.youtube.com/watch?v=b8YUfee_pzc&t=23003s
using System.Collections;
using System.Collections.Generic;
using UnityEngine;


public class Collidable : MonoBehaviour {

	public ContactFilter2D filter;
	private BoxCollider2D boxCollider;
	private Collider2D[] hits = new Collider2D[10];

	protected virtual void Start()
	{
		boxCollider = GetComponent<BoxCollider2D> ();
	}
	protected virtual void Update()
	{
		boxCollider.OverlapCollider (filter, hits);
		for (int i = 0; i < hits.Length; i++) {
			if (hits [i] == null)
				continue;
			OnCollide (hits [i]);

			hits [i] = null;

		}
	}
	protected virtual void OnCollide(Collider2D coll)
	{
		Debug.Log ("My heart and actions are utterly unclouded they are those of justice" + this.name);
	}
}
