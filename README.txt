
question 04

class ContactAdapter extends RecyclerView.Adapter<ContactViewHolder>
implements Filterable {
   private Context context;
   private ArrayList<Drugs> listDrugs;
   private ArrayList<Drugs> mArrayList;
   private SqliteDatabase mDatabase;
   ContactAdapter(Context context, ArrayList<Drugs> listDrugs) {
      this.context = context;
      this.listDrugs = listDrugs;
      this.mArrayList = listDrugs;
      mDatabase = new SqliteDatabase(context);
   }
   @Override
   public ContactViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
      View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.contact_list_layout, parent, false);
      return new ContactViewHolder(view);
   }
   @Override
   public void onBindViewHolder(ContactViewHolder holder, int position) {
      final Drugs drugs = listDrugs.get(position);
      holder.dname.setText(drugs.getname());
      holder.dprice.setText(drugs.getprice());

    }


    //total

    public void setOnClickListener(new view.onClickListner)
    {

        public void onClick(view v){

            Cursor cursor = db.rawQuery("SELECT Totals(" + DbHelper.CART_TOTAL + ") as Total FROM " + DbHelper.CART_TABLE, null);

            if (cur.moveToFirst()) {
           
            int total = cursor.getInt(cursor.getColumnIndex("Total"));// get final total
        }
    }
}



b)


textview Result=findViewById(r.id.amount_to_paid);


payBtn.setOnClickListener(new view.onClickListner(){
    public void onclick(view v){
        if(card.isSuccessful(){
            int discount=total*2/100;
            total=total-discount;
            Result.setText(String.valueOf(total));
            Result.setcolor(color.Red)
 
              }

         if(promo.isChecked(){

                if(promo.get(3).toString().equals("promocode")){
                    promocode.setChecked(true);
                    int discount=total*5/100;
                    total=total-discount;
                    Result.setText(String.valueOf(total));
                    Result.setcolor(color.Red)


                }else{
                    Toast.maketext(getApplicationContext,"Invalid promocode",Toast.LENGTH_SHORT()).show();


                }

              })
              
         )



    }
})

//main 

RecyclerView recyclerView;
    ArrayList<DoctorModel> doctorsList;
    MyAdapter myAdapter;
    doctorsList = new ArrayList<DoctorModel>();
    myAdapter = new MyAdapter(DoctorsView.this,doctorsList,selectedDate,selectedTime);
    recyclerView = findViewById(R.id.recyclerView);
        recyclerView.setHasFixedSize(true);
        recyclerView.setLayoutManager(new LinearLayoutManager(this));

        recyclerView.setAdapter(myAdapter);



//read by boolean
public Boolean check user(String user_id){
    SQLiteDatabase MyDB = this.getReadableDatabase();

    Cursor cursor = MyDB.rawQuery("Select * from users where ID = ? ", new String[] {user_id});
    System.out.println(cursor.getCount());

    if (cursor.getCount() > 0)
        return true;
    else
        return false;
}


public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {

    Context context;
    ArrayList<DoctorModel> doctorsArrayList;
    String date;
    String time;

    public MyAdapter(Context context, ArrayList<DoctorModel> doctorsArrayList, String date, String time) {
        this.context = context;
        this.doctorsArrayList = doctorsArrayList;
        this.date = date;
        this.time = time;
    }

    @NonNull
    @Override
    public MyAdapter.MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {

        View v = LayoutInflater.from(context).inflate(R.layout.item,parent,false);

        return new MyViewHolder(v);
    }

    @Override
    public void onBindViewHolder(@NonNull MyAdapter.MyViewHolder holder, int position) {
        DoctorModel doctorModel = doctorsArrayList.get(position);
        holder.doctorsName.setText(doctorModel.name);
        holder.doctorsEmail.setText(doctorModel.email);


        holder.viewButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(context,DoctorProfile.class);
                context.startActivity(intent);
            }
        });

        holder.appointButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                FirebaseFirestore db = FirebaseFirestore.getInstance();
                AppointmentModel appointmentModel = new AppointmentModel(
                        "",
                        "currentUser",
                        doctorModel.id,
                        date,
                        time,
                        100,false
                );
                db.collection("appointments").document().set(appointmentModel)
                        .addOnCompleteListener(new OnCompleteListener<Void>() {
                            @Override
                            public void onComplete(@NonNull Task<Void> task) {
                                if(task.isSuccessful()){
                                    Toast.makeText(context, "Appointment Created Successfully", Toast.LENGTH_SHORT).show();
                                    Intent intent = new Intent(context,AllAppointmentsActivity.class);
                                    context.startActivity(intent);
                                }else{
                                    Toast.makeText(context, "Create Appointment failed,Try again", Toast.LENGTH_SHORT).show();
                                }
                            }
                        });
            }
        });
    }

    @Override
    public int getItemCount() {
        return doctorsArrayList.size();
    }

    public static class  MyViewHolder extends  RecyclerView.ViewHolder{

        TextView doctorsName,doctorsEmail;
        Button viewButton,appointButton;

        public MyViewHolder(@NonNull View itemView) {
            super(itemView);
            doctorsName = itemView.findViewById(R.id.tvName);
            doctorsEmail = itemView.findViewById(R.id.tvEmail);
            viewButton = itemView.findViewById(R.id.viewDoctorButton);
            appointButton = itemView.findViewById(R.id.createAppointmentButton);


        }
    }
}

// this function is triggered when user
      // selects the image from the imageChooser
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
 
        if (resultCode == RESULT_OK) {
 
            // compare the resultCode with the
              // SELECT_PICTURE constant
            if (requestCode == SELECT_PICTURE) {
                // Get the url of the image from data
                Uri selectedImageUri = data.getData();
                if (null != selectedImageUri) {
                    // update the preview image in the layout
                    IVPreviewImage.setImageURI(selectedImageUri);
                }
            }
        }
    }

// this function is triggered when
      // the Select Image Button is clicked
    void imageChooser() {
 
        // create an instance of the
          // intent of the type image
        Intent i = new Intent();
        i.setType("image/*");
        i.setAction(Intent.ACTION_GET_CONTENT);
 
        // pass the constant to compare it
          // with the returned requestCode
        startActivityForResult(Intent.createChooser(i, "Select Picture"), SELECT_PICTURE);
    }


//a
EditText pharmacyname=(EditText)findViewById(R.id.pharmacyname);
pharmacyname.setenable

//ii
Bundle extras =Intemt .getExtras();
if(extras!=null)
String data =extras.getString(name);
textview.setText(data)

//b
//i
recyclerView

//ii
<String name ="paracetamol">paracetamol</String>
<String name ="vitamin c">vitamin c</String>
<String name ="amoxicillin">amoxicillin</String>

<string-array name="drugs">
    <drugs>@string/paracetamol</drugs>
    <drugs>@string/vitamin</drugs>
    <drugs>@string/amoxicillin</drugs>

</string-array>

//iii
<EditText
android:hint="@string/age"
/>

//c


public void checkboxx(){
    String name=EditTextname.getText().toString().trim();
    String age=EditTextname.getText().toString().trim();

    checkbox.setEnable(name.isChecked()&& !age.isChecked());

}
\

