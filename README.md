# Heap
how to inser and remove in heap

//package prog1;
public class Node {
    String name;
    int Priority;
    public  Node(String name, int Priority)
    {
        this.name = name;
        this.Priority = Priority;
    }
}


//package prog1;
import java.util.Arrays;
public class PriorityQueue {
    int position;
    Node[] NodeArr;
     public PriorityQueue(){
        NodeArr = new Node[255];
        position = 0;
    }
     /*
     Insert name and Priority in array
     */
     public void insert(String name, int Priority){
       
            NodeArr[position] = new Node(name, Priority);
            bubbleUp();
            position +=1;
    }
     /*
     shift big value to parent node
     */
    public void bubbleUp(){
        int pos = position;
        while(pos > 0 && NodeArr[(pos-1)/2].Priority < NodeArr[pos].Priority){
            Node temp = NodeArr[(pos-1)/2];
            NodeArr[(pos-1)/2] = NodeArr[pos];
            NodeArr[pos] = temp;
            pos = (pos-1)/2;
        }
    }
    /*
    remove the max priority from array
    */
    public String remove(){
            Node temp2 = NodeArr[0];    
            NodeArr[0] = NodeArr[position -1];
            position--;
            bubbleDown(0);
            return temp2.name;
    }
    /*
    move the smaller value to chile node
    */
    public void bubbleDown(int n){
       Node temp1 = NodeArr[n];
      int max = n;
      int lC = (2*n)+1;
      int rC = (2*n)+2;
      if(lC < position && NodeArr[max].Priority < NodeArr[lC].Priority){
        max = lC;
        }
      if(rC < position && NodeArr[max].Priority < NodeArr[rC].Priority){
        max = rC;
        }
      if(max != n){
          Node temp2 = NodeArr[n];
          NodeArr[n] = NodeArr[max];
          NodeArr[max] = temp1;
          bubbleDown(max);
        }
    }
}

//package prog1;
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Arrays;
import java.util.Scanner;

public class Prog1 {
    public static void main(String[] args) throws FileNotFoundException {
     
       Scanner input = new Scanner("C:/Users/Aliza/Desktop/input.txt");
       PriorityQueue m = new PriorityQueue();
       String[] arr = new String[300];
       int a = 0, i =0;
       while(input.hasNext())
       {
        arr[a] = input.next();
        a++;
       }
       while(arr[i] != null)
       {
           if(arr[i].compareTo("insert") == 0){
              m.insert(arr[i + 1], Integer.parseInt(arr[i+2]));
              i = i+3;
           }
           else
           {
               System.out.println(m.remove());
               i = i+1;
           }
       }
    }
    
}


