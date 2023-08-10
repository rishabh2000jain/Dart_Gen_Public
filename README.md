# Dart Gen
<br/>
<h2>Tool Description </h2>
<br/>
<li>In this fast-moving world <a href="https://dartgen-eb7ad.web.app/#/">Dart Gen</a> aims to reduce the coder's manual efforts to as low as possible</li>
<li><a href="https://dartgen-eb7ad.web.app/#/">Dart Gen</a> is an excellent tool for generating API Response Models, Ui Models, and mapper to map data.</li>
<li>Within a few seconds, this tool can generate code that might take 20-30 mins if done manually and it generates code that is completely null safe.</li>
<br/>
<h2>Future Release For <a href="https://dartgen-eb7ad.web.app/#/">Dart Gen</a></h2>
<br/>
<li>In future releases I will be working on making it simpler so that Retrofit API calls class, Request Model, and the models it is generating as of now can be generated in one click</li>
<li>Within a few seconds, this tool can generate code that might take 20-30 mins if done manually and it generates code that is completely null safe.</li>

<h1>Sample Code</h1>
<h2>
  JSON
</h2>
<pre>
  <code>
  {
   "status": "success",
   "data": [
      {
         "id": 1,
         "employee_name": "Tiger Nixon",
         "employee_salary": 320800,
         "employee_age": 61,
         "profile_image": ""
      },
      {
         "id": 2,
         "employee_name": "Garrett Winters",
         "employee_salary": 170750,
         "employee_age": 63,
         "profile_image": ""
      }
   ],
   "message": "Successfully! All records has been fetched."
}
  </code>
</pre>

</br>

<h2>
  Response Model
</h2>

<pre>
  <code>
    import 'package:json_annotation/json_annotation.dart';
    import 'employee_data_response_model.g.dart';


    @JsonSerializable()
    class EmployeeDataResponseModel{
        @JsonKey(name: 'status')
        String? status;

        @JsonKey(name: 'data')
        List<Data>? data;

        @JsonKey(name: 'message')
        String? message;
    }


    @JsonSerializable()
    class Data{
        @JsonKey(name: 'id')
        int? id;

        @JsonKey(name: 'employee_name')
        String? employeeName;

        @JsonKey(name: 'employee_salary')
        int? employeeSalary;

        @JsonKey(name: 'employee_age')
        int? employeeAge;

        @JsonKey(name: 'profile_image')
        String? profileImage;
    }

  </code>
</pre>
<h2>
  UI Model
</h2>

</br>
<pre>
  <code>
      class EmployeeData{
            String status;
            List<Data> data;
            String message;
      }
      class Data{
            int? id;
            String employeeName;
            int employeeSalary;
            int employeeAge;
            String profileImage;
      }
  </code>
</pre>

<h2>
 Mapper Class
</h2>

</br>
<pre>
  <code>
     import 'employee_data_response_model.dart';
     import 'employee_data.dart';
      class EmployeeDataMapper {
            EmployeeData call(EmployeeDataResponseModel employeeDataResponseModel) {
                        return EmployeeData(
                                status: (employeeDataResponseModel.status) ?? "",
                                data: (employeeDataResponseModel.data?.map(
                                (dataItem) => Data(
                                              id: (dataItem.id) ?? 0,
                                              employeeName: (dataItem.employeeName) ?? "",
                                              employeeSalary: (dataItem.employeeSalary) ?? 0,
                                              employeeAge: (dataItem.employeeAge) ?? 0,
                                              profileImage: (dataItem.profileImage) ?? "",
                                              ),
                                  ))?.toList() ??[],
                          message: (employeeDataResponseModel.message) ?? "",
              );
      }
}


  </code>
</pre>
