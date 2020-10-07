# javaRush1710

package com.javarush.task.task17.task1710;

import java.io.IOException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.Locale;

/* 
CRUD
*/

public class Solution {
    public static List<Person> allPeople = new ArrayList<Person>();

    static {
        allPeople.add(Person.createMale("Иванов Иван", new Date()));  //сегодня родился    id=0
        allPeople.add(Person.createMale("Петров Петр", new Date()));  //сегодня родился    id=1
    }

    public static void main(String[] args) throws IOException, ParseException {
        //start here - начни тут

        if (args[0].equals("-c"))
        {
            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/YYYY", Locale.ENGLISH);
            String name = args[1];
            Date bd = dateFormat.parse(args[3]);

            if (args[2]=="м")
            {
                Person man = Person.createMale(name,bd);
                allPeople.add(man);
                System.out.println(man);
            }
            else if (args[2]=="ж")
            {
                Person woman = Person.createFemale(name,bd);
                allPeople.add(woman);
                System.out.println(woman);
            }
        }

        if (args[0].equals("-u"))
        {
            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/YYYY", Locale.ENGLISH);
            String id = args[1];
            int idArray = Integer.parseInt(id);
            String name = args[2];
            Date db = dateFormat.parse(args[4]);

            if (args[3]=="м")
            {
                allPeople.add(idArray,Person.createMale(name,db));
            }
            else if (args[3]=="ж")
            {
                allPeople.add(idArray,Person.createFemale(name,db));
            }
        }

        if (args[0].equals("-d"))
        {
            String id = args[1];
            int idArray = Integer.parseInt(id);
            allPeople.get(idArray).setName(null);
            allPeople.get(idArray).setSex(null);
            allPeople.get(idArray).setBirthDate(null);
        }

        if (args[0].equals("-i"))
        {
            SimpleDateFormat dateFormat = new SimpleDateFormat("dd-MMM-YYYY", Locale.ENGLISH);
            String id = args[1];
            int idArray = Integer.parseInt(id);
            System.out.println();
        }

    }
}
