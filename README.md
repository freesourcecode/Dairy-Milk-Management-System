# Dairy Milk Management System Project in Django with Source Code

The **Dairy Milk Management System Project in Django** created based on python, Django, and SQLITE3 Database.

The **Dairy Management System** is a software-based program that functions as a dairy software to keep track of daily milk production for registered account members (dairy manager). Customers can access the customer ledger page by logging in.

A **Dairy Milk Management System in Django** is an easy project for beginners to learn how to build a web-based python Django project.

We will provide you with the complete source code and database for the python project so that you can easily install it on your machine and learn how to program in Python Django.

>[!NOTE]
> To start creating a **Dairy Milk Management System Project in Python Django**, makes sure that you have PyCharm Professional IDE Installed in your computer.

## Dairy Milk Management System Project in Django: Admin Features

* The admin account can be created using createsuperuser command.
* Administrator Can Add Vendors.
* Administrator Can Add Milk Category For Related Vendor.
* Admin Can See All The Vendors Dashboard.
* Admin Can See The Individual Vendor Ledger.
* Administrator Can Add Customers After Register An User.
* Admin Can Add Milk Category For Related Customer.
* Admin Can See All The Customers Dashboard.
* Administrator Can See The Individual Customer Ledger.

## How to Create a Project Dairy Milk Management System in Django?

Here are the steps on how to create a **Dairy Milk Management System Project in Django with Source Code**.

1. **Open file**.

Open “pycharm professional” after that click “file” and click “new project”.

2. **Choose Django**.

After click “new project“, choose “Django” and click.

3. **Select file location**.

Then, select a file location wherever you want.

4. **Create application name**.

After that, name your application.

5. **Click create**.

Lastly, finish creating project by clicking “create” button.

6. **Start Coding**.

Finally, we will now start adding functionality to our Django Framework by adding some functional codes.


## Functionality and Codes of the Dairy Milk Management System Project in Django with Source Code

* **Create template for the add customer form in Dairy Milk Management System Project in Django**.

In this section, we will learn on how create a templates for the add customer form. 

To start with, add the following code in your add_customer.html under the folder of /templates/.

```
{% extends 'base.html' %}
{% load crispy_forms_tags %}


{% block content %}
<style>
  #back {
    /* background-image: linear-gradient(to top, #d5d4d0 0%, #d5d4d0 1%, #eeeeec 31%, #efeeec 75%, #e9e9e7 100%); */
    background-color: #2B2D33;
    color: #B8C6CC;
  }

  .form-control{
    background-color: #2B2D33!important;
    color: #B8C6CC!important;
  }
</style>

<div class="row justify-content-center">
  <div class="col-10">
    <div id="back" class="card">
      <div class="card-body">
        <h2 class="mb-4">Add Customer</h2>
        <hr>
        <form method="POST" novalidate>
          {% csrf_token %}

          <div class="form-row">
            <div class="form-group col-md-4">
              {{ form.user|as_crispy_field }}
            </div>

            <div class="form-group col-md-4">
              {{ form.user_type|as_crispy_field }}
            </div>

            <div class="form-group col-md-4">
              {{ form.contact_number|as_crispy_field }}
            </div>
          </div>



          <div class="form-row">
            <div class="form-group col-md-4">
              {{ form.joining_data|as_crispy_field }}
            </div>
            <div class="form-group col-md-8">
              {{ form.address|as_crispy_field }}
            </div>
          </div>

          <button type="submit" class="btn btn-dark">Save</button>
        </form>
      </div>
    </div>
  </div>
</div>
{% endblock %}
```

* **Create template for the customer ledger form in Dairy Milk Management System Project in Django**.

In this section, we will learn on how create a templates for the customer ledger form. 

To start with, add the following code in your customer_ledger.html under the folder of /templates/.

```
{% extends 'base.html' %}
{% load crispy_forms_tags %}
{% load templatetags %}


{% block content %}
<style>
  .form-control{
    background-color: #2B2D33!important;
    color: #B8C6CC!important;
  }
  select:focus {
    background-color: #2B2D33!important;
    color: #B8C6CC!important;
  }
  option:focus {
    background-color: #2B2D33!important;
    color: #B8C6CC!important;
  }
  input:focus {
    background-color: #2B2D33!important;
    color: #B8C6CC!important;
  }
</style>

<h2 class="vendor_name_heading"><strong>{{ customer_full_name }}</strong></h2>


<div class="table-responsive">
        <table class="table table-bordered">
          <thead>
              <tr>
                <th scope="col">Customer</th>
                <th scope="col">Date</th>
                <th scope="col">Milk Type</th>
                <th scope="col">Quantity(Liter)</th>
                <th scope="col">Save</th>
              </tr>
            </thead>

        <tbody>
          <form action="\customer_ledger_save\" method="POST">
            {% csrf_token %}
              <tr>
               <td scpoe="col">
                 <div class="form-row">
                   <div class="col">
                     <select class="form-control" id="customer" name="customer">
                          <option value="{{ customer_obj.pk }}"> {{ customer_obj.first_name }} {{ customer_obj.last_name }} </option>
                        </select>
                        </div>
                      </div>
                      </td>

                <td scpoe="col">
                  <div class="form-row">
                    <div class="col">
                      <p><input class="form-control" type="text" name="date" id="datepicker"></p>
                    </div>
                  </div>
                </td>
                <td scpoe="col">
                  <div class="form-row">
                    <div class="col">
                      <select  class="form-control" id="milktype" name="milktype">
                        {% for milk, milk_pk in milk_list %}
                        <option value="{{ milk_pk }}"> {{milk}} </option>
                        {% endfor %}
                      </select>
                    </div>
                  </div>
                </td>
                <td scpoe="col">
                  <div class="form-row">
                    <div class="col">
                      <input type="name" class="form-control"  name="quantity" placeholder="0"  pattern="\d+">
                    </div>
                  </div>
                </td>
                <td scpoe="col">
                  <div class="form-row">
                    <div class="col">
                      <button type="submit" class="btn btn-dark border"><i class="fas fa-save" style="background-color: unset !important;">&nbsp;&nbsp;Save</i></button>
                    </div>
                  </div>
                </td>
              </tr>
            </form>


            </tbody>
        </table>
    </div>



  <div class="table-responsive">
      <table class="table table-bordered table-striped ">


        <thead id="theadthid">
          <tr >
                <th scope="col">No.</th>
                <th scope="col">Date</th>
                <th scope="col">Milk Category</th>
                <th scope="col">Price</th>
                <th scope="col">Quantity</th>
                <th scope="col">Total</th>
                <th scope="col">Delete</th>
            </tr>
        </thead>

        <tbody id="tbodydata">
          {% for ledger in customer_ledger_info %}

          <tr>
            <th scope="row">{{ forloop.counter }}</th>
            <td>{{ ledger.date }}</td>
            <td>{{ ledger.related_milk_category }}</td>
            <td>{{ ledger.price }} Tk.</td>
            <td> {{ ledger.quantity }} L</td>
            <td>{% multiply ledger.quantity ledger.price %} Tk.</td>


            <td>
              <form action="{% url 'customer_ledger_delete' %}" method="POST">{% csrf_token %}
                <button class="btn btn-danger"type="submit" name="customer_pk" value="{{ledger.pk}}"><i class="far fa-trash-alt" style="background-color: unset !important; color: unset !important;">&nbsp;&nbsp;Delete</i></button>
                </form>
                </td>
          </tr>
{% endfor %}
<tr>
<td colspan="4"></td>
<td id="totalid"><strong>Grand Total - {{ alltotal }} Tk.</strong></td>
</tr>
          </tbody>
      </table>
  </div>
<!-- Script for datepicker -->
<!-- <script>
$( function() {
  $( "#datepicker" ).datepicker();
  $( "#datepicker" ).datepicker("show");

  // $( "#datepicker" ).datepicker("setDate","0");
} );
</script> -->
<script>
  $(function() {
      $( "#datepicker" ).datepicker({dateFormat:"dd-mm-yy",});

  });
</script>


{% endblock %}
```
### 📌 Here's the full documentation for the [Dairy Milk Management System Project](https://itsourcecode.com/free-projects/python-projects/dairy-milk-management-system-project-in-django-with-source-code/)
