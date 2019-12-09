# Add-and-Remove-Buttons
https://bearnithi.com/2019/05/25/add-remove-multiple-input-fields-dynamically-template-driven-angular/
 
<!---- html---->
<form #addressForm="ngForm" class="container mt-3" (ngSubmit)="logValue()">
  <!-- some code here - see full code at the end of this tutorial -->
   <section *ngFor="let address of addresses; let i = index;">
      <!-- input fields inside the *ngFor -->
         <label>Address</label>
         <input type="text" [(ngModel)]="address.address"
           name="address_{{i}}"/>
         <label>Street</label>
         <input type="text" [(ngModel)]="address.street"
           name="street_{{i}}"/>
         <label>City</label>
         <input type="text" [(ngModel)]="address.city"
           name="city_{{i}}"/>
         <label>Country</label>
         <select [(ngModel)]="address.country" name="country_{{i}}" placeholder="India">
               <option value="india">India</option>
               <option value="usa">USA</option>
                <option value="england">England</option>
         </select>
   </section>
 </form>

<!----------ts.---->
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  public addresses: any[] = [{
    address: '',
    street: '',
    city: '',
    country: ''
  }];
  constructor() {

  }

  ngOnInit() {

  }

  addAddress() {
    this.addresses.push({
      address: '',
      street: '',
      city: '',
      country: ''
    });
  }

  removeAddress(i: number) {
    this.addresses.splice(i, 1);
  }

  logValue() {
    console.log(this.addresses);
  }
}
<!------css---->
$color-primary: rgba(67,66,93,255);
$color-text: #43425d;
$color-text-lite: rgba(#4d4f5c,.5);

.login-container {
    font-family: "Source Sans Pro";
    .sidebar {
        background-image: url(/assets/images/group_4.png), 
              linear-gradient(-136.82353093203deg , rgba(36,35,72,255) 0%, rgba(90,85,170,255) 100%);
        background-size: cover;
        min-height: 100vh;
    }

    .title, a {
        color: $color-text;
    }

    .title {
        font-weight: bold;
        letter-spacing: 5px;
    }

    .tag {
        color: $color-text-lite
    }

    .btn-main {
        background: $color-primary;
    }

    .btn-main-outline {
        border: 1px solid $color-primary
    }

}
