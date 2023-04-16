# SinglyLinkedList-SistemManajemenKeretaApi

import  java.util.*;

public class SLL_KeretaApi {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        SLLKeretaApi <Object> list = new SLLKeretaApi <>();


        String kereta = input.nextLine();
        boolean isTrue=true;
        while(isTrue){
            String kode = input.nextLine();
            if (kode.equals("CETAK")){
                System.out.println(kereta);
                list.display();
                break;
            }
            String[] arr = kode.split(" ");
            if(arr[0].equals("TAMBAH")){
                list.add(arr[1]);
            } else if (arr[0].equals("LEPAS")){
                list.remove(Integer.parseInt(arr[1]));
            }
        }
    }
}
class SLLKeretaApi<T>{
    Node head;
    Node tail;

    void add (String data){
        if(head==null){
            head = new Node(data);
            tail= head;
        } else {
            tail.next=new Node(data);
            tail=tail.next;
        }
    }
    void remove (int index){
        if(head==null){
            return;
        }
        if (index == 0 ) {
            this.head = this.head.next;
            return;
        }
        Node currentNode = head;
        for (int i = 0;i<index-1;i++){
            currentNode = currentNode.next;
        }
        currentNode.next = currentNode.next.next;
        if (currentNode.next == null){
            tail = currentNode;
        }
    }
    void display (){
        if(head == null){
            return;
        }else {
            Node temp = head;
            while(temp != null){
                if (temp.next == null){
                    System.out.print(temp.data);
                    break;
                }
                System.out.print(temp.data + "-");
                temp = temp.next;
            }
        }
    }
}

class Node{
    String data;
    Node next;
    Node (String data){
        this.data = data;
    }
}
