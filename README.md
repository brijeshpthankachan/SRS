




# Software Requirements specification 


`myDoctor is a Doctor appointment services management App. Their high level requirements are as
follows.`

## 1.  Login facility with two authentication such as captcha and a picture [OTP via email]
> ### 1.1  user should be able to register providing
>---
>>- 1.1.1 `Email`   *[unique] [ validation for email]*
>>- 1.1.2 `Phone Number` *[Unique] [ maximum of 10 numbers ]* + [country code] [ **referd in requiremtnt 1.2**  ]
>>- 1.1.3 `password` *[required][minlength(6) include special ACharacters, Uppercase & Lower Case & Number]*
>>- 1.1.4 `Confirm password`  
>---
> ### 1.2 user must fill a detailed form to register for services.it should include [ patient Details component ]
>---
>   [phone number] refered as foreign key
>>- `First Name` *[ required min length 1, maxlength (20) ]*
>>- `Last Name` *[cannot contain numbers , maxlength (20)]* 
>>- `date of birth` [ date ] [required] 
>>- `Gender` [ dropdown (male,female,other) ][required]
>>- `House No` [required ][maxlength (25)]
>>- `Place` [required] [max length(25)]
>>- `Pincode` [number ] [6 digits min & max]
>>- `Emergency Contact Number` [10 digits]
>>- `Blood Group` [ drop down ]
>>- `Aadhar Number` [number 12 digits unique]
>>- `relation`[spouse] [parent]  [child] [friend] [relative] (for first time registration realationship field should be assigned as [self])


## 2. Logined Users should Be able to perform the following Tasks
>- 2.0 **Patient Home page should include incomplete bookings with booking number and print bill  and memebr options**
>---
>- 2.1 **Add Aditional Family Members upto a maximum of 6 members. [using details component ]**
>---
>-  2.2 **able to update details of members.** 
>--- 
>>- 2.2.1 there should be an edit button for each associated members.
>>- 2.2.2 Editable fields are `house No`, `Place`, `Pincode`, `Emergency Contact Number`, `Gender` 
>----
>-  2.3 **must be able to book appointments for he/she as well as registered members.**
>---
>>- 2.3.1 user should be able to book for an appinment by clicking book appointment by clicking appintment button on the navigation bar.
>>- 2.3.2 user should be ble to filter doctors by departments and availbaility
>>- appoinment details should contain
>>>- `Date and time` [cannot be a previous date] 
>>>- `Session` [morning, afternoon, evening] [if peak hour additional charge will be there]
>>>- `Department` [ drop down  ]
>>>- `Doctor name` [ department filtered available doctors ]  
>>- `After Succesfull booking redirect to payment page / the page should contain current booking details with additional details`
>>>- `Consultation Fee` [ Adjusted for peakhour ]
>>>- `Tax`
>>>- `Payment Options` [upi,card]
>>>- `Confirm Booking` ('succesfull payment should redirect user to bookings Home`)
>>>- Home should display current booking at top of bookings table `along with the cancel & Edit Booking option`.
>>>- Cancel and edit option must be disabled for completed consuktations
>>>- Booking Status Should be maintained [completed][not completed] [parked]
>---
>-  2.4 **user must be able to see past prescreptions** `[ able to filter by date, disease, doctor ]`
>---
>-  2.5 **user must be able to see past diagnostics** `[ able to filter by date, disease, doctor ]`
>---
>- 2.6 **navbar links are** [Home] [Book Appintment] [Doctors] [Consultation history] [Logout]
>---

## 3 Doctors search facility  
>>- 3.1 search filtered basis of department
>----
>>>- 3.1.1 Result should be available in a paginated table
>>>- 3.1.2 result raw should include view Details button along with doctor name and department, gender [ `details button shows details pane` ]
>>>---
>>>> - 3.1.2.1 details tab should include  `avatar` `dr. firstname lastname`, `gender`, `specilization`, `qualification`, `years of experiance` `contact number`, `email`, `availability` [ go back button shows results table ]


## 4.  Doctors master details shall be captured  
>-  4.1 Adminstrator should be able to add a doctor providing following details.  
>   *[references primary key of identity table]*
>----
>>- `first name`
>>- `last name` 
>>- `gender`
>>- `specilaization`
>>- `qualification`
>>- `years of experiance`
>>- `contact number`
>>- `dob`
>>- `availability`
>--------------
> *[should be stored in the identity table with role doctor]* 
>>- `email` [ 'email is unique`] 
>>- `password`
>>- `Confirm Passowrd`

>-  4.2 a doctor with an account should be able to sign in using credentials given by the admin 
>>- 4.2.1 signed in doctor should be able to view his Consultation  requests for that [ `paginated` `soreted based on time`, `session`,`incompleted`  ] 
>>- 4.2.2 each consult request table should have a consult button [ `consult button will be redirected to consultation page` ]
>>>- 4.2.2.1 consultation page should contain
>>>>- preavius consultation details [ dropdown ]
>>>>- past medication details  [ details of selected consultaion ]
>>>>- patient basic info  [name] [age] [gender] [blood group] [Bp][Sugar][temperature]
>>>- 4.2.2.2 Current Consultation Pane (should contain)
>>>>- current dignosis [ text area ]
>>>>- prescrptions [ different pane for injection and tablets ]
>>>>- medication timing for each mediines 

```
ac (ante cibum) means "before meals"
bid (bis in die) means "twice a day"
gt (gutta) means "drop"
hs (hora somni) means "at bedtime"
od (oculus dexter) means "right eye"
os (oculus sinister) means "left eye"
po (per os) means "by mouth"
pc (post cibum) means "after meals"
prn (pro re nata) means "as needed"
q3h (quaque 3 hora) means "every three hours"
qd (quaque die) means "every day"
qid (quater in die) means "four times a day"
Sig (signa) means "write"
tid (ter in die) means "three times a day"
```
>>>>- Radiology option
>>>>>- `ECG`,  `X-Ray`, `MRI`, `EEG`, `EMG`, `Ultrasound`, `CT`, `PET`, `Echocardiogram`, `Angiography`
>>>>- Lab Tests

``` 
amniocentesis
blood analysis
blood count
blood typing
bone marrow aspiration
cephalin-cholesterol flocculation
enzyme analysis
epinephrine tolerance test
glucose tolerance test
hematocrit
immunologic blood test
inulin clearance
serological test
thymol turbidity
gastric fluid analysis
kidney function test
liver function test
lumbar puncture
malabsorption test
Pap smear
phenolsulfonphthalein test
pregnancy test
prenatal testing
protein-bound iodine test
syphilis test
thoracentesis
thyroid function test
toxicology test
urinalysis/uroscopy

```

>>>>- remarks field
>>>>-----
>>>- doctor should be able to submit and complete consultation or park a patient for recalling
>>>- doctor should be able to see parked patients in a seperate window and recall

>> 4.3 additional features for doctor
>-----
>>>- `view profile`
>>>- `view past consultations`


## 5. Prescription shall be visible to  Pharmacy folks
>- 5.1 Admin should create a login credentials for pharmacy folks
>- 5.2 Phrmacy folks should be able to see prescrptions for current day
>- 5.3 able to issue an invoice [ medicine name ][price] [taxt] [net price]
>- 5.4 payment option additional by cash facility.
>- print bill 



## 6. Feedback shall be collected
>>- 6.1 able to provide rating for doctor as well as overall services
>>- 6.2 admin should be able to see feedbacks along with patient name
