<template>
  <div id="app">
    <h1>
      <img src="./assets/Vue_Nuggets.png" alt="" />
    </h1>
    <h1 class="default-color">
      E-commerece Nuggets are now available as a <a href="https://www.npmjs.com/package/ecommerce-ui-nuggets">NPM Package</a> 🎉 🎉 🎉
    </h1>
    <div class="card">
      <Alert :isActive="this.errorActive">Error Message Goes Here</Alert>
      <Alert alertType="warning" alertPosition="global" :isActive="this.warnActive" :persistFor="5">Warning Message Goes Here</Alert>
      <h1>
        Quantity Selector
      </h1>
      <p class="card-text">
        6 configirable properties
        <ol>
          <li>count - Default value <strong>1</strong></li>
          <li>maxCount - Default value <strong>6</strong></li>
          <li>isCountEditable - Default value <strong>true</strong></li>
          <li>iconDimensions - Default value <strong>15</strong></li>
          <li>minusIconFillColor - Default value <strong>#000</strong></li>
          <li>plusIconFillColor - Default value <strong>#000</strong></li>
        </ol>
      </p>
      <p class="card-text">
        Count of the component is emitted to the parent copmponent using a custom event <strong class="highlight-text">get-count</strong>
      </p>
      <div>
    </div>
      <div class="card-text">
        <h4>Default</h4>
        <QuantitySelector />
        <Alert :isActive="this.inlineErrorActive" alertPosition="inline">Error Message Goes Here</Alert>
      </div>
      <div class="card-text">
        <h4>Min count set to 4</h4>
        <QuantitySelector :count="4" />
      </div>
      <div class="card-text">
        <h4>All properties configured</h4>
        <QuantitySelector :isCountEditable=false :count="2" :maxCount="10" :iconDimensions="15" minusIconFillColor="red" plusIconFillColor="green" />
      </div>
      <div class="card-text">
        <h4>stepInterval of more than 1 is used. (Use case, selling print materials online!)</h4>
        <QuantitySelector :isCountEditable=false :count="1" :maxCount="17" :stepInterval="2" :iconDimensions="16" minusIconFillColor="red" plusIconFillColor="green" />
      </div>
      <div class="card-text">
        <h4>stepInterval of more than 1 is used. maxCount is not a multiple of stepInterval and count</h4>
        <QuantitySelector :isCountEditable=false :count="3" :maxCount="17" :stepInterval="3" :iconDimensions="16" minusIconFillColor="red" plusIconFillColor="green" />
      </div>
      <div class="card-text">
        <h4>
          Emit the quantity from component to parent component when tha parent needs to know about the selected quantity.
        </h4>
        <div class="compo-label">
          <strong class="highlight-text">Quantity: {{ this.getCountVal }}</strong>
        </div>
        <QuantitySelector @get-count="passCountVal" />
      </div>
    </div>

    <div class="card">
      <h1>
        Star Rating
      </h1>
      <p class="card-text">
        7 configirable properties
        <ol>
          <li>rating - There is no default value.</li>
          <li>totalStars - Default value <strong>5</strong></li>
          <li>iconDimensions - Default value <strong>20</strong></li>
          <li>baseColor - Default value <strong>#CCC</strong></li>
          <li>fillColor - Default value <strong>#42b983</strong></li>
          <li>noRatingMsg - Default value <strong>Be the first to review!</strong></li>
          <li>totalReviews - There is no default value.</li>
        </ol>
      </p>
      <div class="card-text">
        <h4>Default</h4>
        <StarRating :rating="0.5" />
        <Alert :isActive="this.inlineWarnActive" alertType="warning" alertPosition="inline" :persistFor="30">Warning Message Goes Here</Alert>
      </div>
      <div class="card-text">
        <h4>Default</h4>
        <StarRating :rating="3.3" totalReviews="113" />
      </div>
      <div class="card-text">
        <h4>No rating</h4>
        <StarRating />
      </div>
      <div class="card-text">
        <h4>Number of base stars id 7</h4>
        <StarRating :rating="4.7" :totalStars="7" :iconDimensions="20" :totalReviews="1029" />
      </div>
      <div class="card-text">
        <h4>fillColor is green and baseColor is #CCC</h4>
        <StarRating :rating="2.4" fillColor="#9b42b9" baseColor="#CCC" />
      </div>
    </div>

    <div class="card">
      <h1>
        Grid
      </h1>
      <p class="card-text">
        Just 1 configirable property
        <ol>
          <li>columns - Default value is an object
            <strong>
              <code>
                {
                  xs: 2,
                  sm: 2,
                  md: 3,
                  lg: 4
                }
              </code>
            </strong>, but can also take a number instead of an object.
          </li>
        </ol>
        <span style="color: red;"><strong>Note:</strong> The dashed border in the Grid items is only part of the demo!</span>
      </p>
      <div class="card-text">
        <h4>Default Grid (Can be used for building a Search/ Browse like page)</h4>
        <Grid>
          <GridItem v-for="(item, index) in gridData" :key="index" >
            <p>
              Product Name can go here!
            </p>
              <StarRating :rating="item.rating" />
            <p>
              Product Description can go here!
            </p>
          </GridItem>
        </Grid>
      </div>
      <div class="card-text">
        <h4>Grid with custom number of columns (Can be used for building a Search/ Browse like page)</h4>
        <Grid :columns="{xs: 1, sm: 2, md: 3, lg: 5}">
          <GridItem v-for="(item, index) in gridData" :key="index" >
            <p>
              Product Name can go here!
            </p>
              <StarRating :rating="item.rating" fillColor="#9b42b9" />
            <p>
              Product Description can go here!
            </p>
          </GridItem>
        </Grid>
      </div>
      <div class="card-text">
        <h4>Proucts scroll (Can be used for features like "Suggested Proucts" or "Recommended Products" or "Shop the Look")</h4>
        <Grid :columns="8">
          <GridItem v-for="(item, index) in gridData" :key="index" >
            <p>
              Product Name
            </p>
              <StarRating :rating="item.rating" fillColor="rgb(27, 149, 224)" baseColor="#CCC" />
            <p>
              Product Description
            </p>
          </GridItem>
        </Grid>
      </div>
    </div>
    <div class="card">
      <h1>
        Alert
      </h1>
      <p class="card-text">
        4 configirable property
        <ol>
          <li>alertType - Default value <strong>error</strong></li>
          <li>alertPosition - Default value <strong>global</strong></li>
          <li>isActive - Default value <strong>false</strong></li>
          <li>persistFor - There is no default value</li>
        </ol>
      </p>
      <div class="card-text">
        <h4>Default</h4>
        <p>
          In a real world use case, some sort of an action will invoke the global error or warning.<br />
          For this demo, the button click will invoke the alert!
        </p>
        <button @click="setActive">{{this.errorActive ? 'Hide Global Error' : 'Show Global Error'}}</button>
      </div>
      <div class="card-text">
        <h4>Global, page-level warning alert that persists only for 5 seconds</h4>
        <p>
          Persistance of the error message signifies the time for which the alert will be shown and then it will disappear!<br />
          The time is expected in seconds! The component will convert it to milli-seconds.
        </p>
        <button @click="setWarnActive">{{this.warnActive ? 'Hide Global Warning' : 'Show Global Warning'}}</button>
      </div>
      <div class="card-text">
        <h4>Inline field-level error alert</h4>
        <p>
          In real world scenarios, a filed level error can be shown when client-side validations are done!
        </p>
        <button @click="setInlineErrorActive">{{this.inlineErrorActive ? 'Hide Inline Error' : 'Show Inline Error'}}</button>
      </div>
      <div class="card-text">
        <h4>Inline field-level warning alert</h4>
        <p>
          In real world scenarios, a filed level warning can be shown when client-side validations are done. Warnings are usually shown and then disappear after a certain time duration.
        </p>
        <button @click="setInlineWarnActive">{{this.inlineWarnActive ? 'Hide Inline Warning' : 'Show Inline Warning'}}</button>
      </div>
    </div>
    <div class="card">
      <h1>
        Bag Count
      </h1>
      <p class="card-text">
        6 configirable properties
        <ol>
          <li>iconDimensions - Default value <strong>40</strong></li>
          <li>iconPath - Default value <strong>M177.91,55.377h-22.589v-1.368C155.311,24.25,131.091,0,101.302,0C71.503,0,47.292,24.25,47.292,54.009v1.368H24.704L11.495,202.614h179.624L177.91,55.377L177.91,55.377z M101.302,6.624c19.687,0,36.619,12.105,43.761,29.232c-9.448-14.137-25.5-23.478-43.761-23.478c-18.231,0-34.313,9.34-43.77,23.507C64.713,18.729,81.635,6.624,101.302,6.624z M57.297,55.377c4.406-20.263,22.481-35.485,44.024-35.485c21.582,0,39.618,15.222,44.024,35.485H57.297z</strong></li>
          <li>fillColor - Default value <strong>#42b983</strong></li>
          <li>fontSize - Default value <strong>80</strong></li>
          <li>fontColor - Default value <strong>#FFF</strong></li>
          <li>bagCount - There is no default value</li>
        </ol>
      </p>
      <div class="card-text">
        <h4>Default</h4>
        <BagCount :bagCount="12" />
      </div>
      <div class="card-text">
        <h4>Custom Bag Icon</h4>
        <BagCount iconPath="M166.089,42.803h-37.671V28.026C128.418,12.573,115.849,0,100.396,0S72.37,12.573,72.37,28.026
		v14.777H36.839l-9.087,157.942h145.24L166.089,42.803z M78.679,28.026c0-11.971,9.745-21.716,21.716-21.716
		c11.975,0,21.713,9.745,21.713,21.716v14.777H78.679V28.026z M42.794,49.109H72.37v14.788h6.31V49.109h43.433v14.788h6.31V49.109
		h31.637l6.345,145.341H34.434L42.794,49.109z" fontColor="#B94278" fillColor="#B94278" :bagCount="5" />
      </div>
    </div>
    <div class="card">
        <h1>
          Variance Selector
        </h1>
        <p class="card-text">
          4 configurable properties
          <ol>
            <li>labelName - Default value <strong>Type</strong></li>
            <li>labelDefaultValue - Default value <strong>Please select one of the following</strong></li>
            <li>varianceData - This is an array of objects, but there is no default value</li>
            <li>shape - Default value <strong>square</strong></li>
          </ol>
        </p>
        <p class="card-text">
          Selected value of the variance component is emitted to the parent copmponent using a custom event <strong class="highlight-text">get-selected-variant</strong>
        </p>
        <div class="card-text">
          <h4>Default (Size Picker)</h4>
          <VarianceSelector labelName="Size" labelDefaultValue="Please select a size" :varianceData="sizeSelectorData" />
        </div>
        <div class="card-text">
          <h4>Default (Color Picker)</h4>
          <VarianceSelector labelName="Color" labelDefaultValue="Please select a color" :varianceData="colorSelectorData" shape="circle" />
        </div>
        <div class="card-text">
          <h4>Default (Quantity Selector)</h4>
          <p>
            Use-case when you have a product sold in bulk, like print paper or visiting cards!
          </p>
          <VarianceSelector labelName="Quantity" labelDefaultValue="Please select quantity" :varianceData="quantitySelectorData" />
        </div>
        <div class="card-text">
          <h4>Size Picker with only ine size!</h4>
          <VarianceSelector labelName="Size" labelDefaultValue="Please select a size" :varianceData="singleSizeData" />
        </div>
        <div class="card-text">
        <h4>
          Emit the selected variant value from component to parent component when tha parent needs to know about the selected value.
        </h4>
        <div class="compo-label">
          <strong class="highlight-text">Selected Variant: {{ this.getVariantVal }}</strong>
        </div>
        <VarianceSelector labelName="Size" labelDefaultValue="Please select a size" :varianceData="sizeSelectorData" @get-selected-variant="passVariantVal" />
      </div>
    </div>
    <div class="card">
        <h1>
            Scroll To Top
        </h1>
        <p class="card-text">
            4 configirable properties
            <ol>
                <li>iconDimensions - Default value <strong>20</strong></li>
                <li>iconPath - Default value <strong>M5.906,34.998c-1.352,1.338-3.541,1.338-4.893,0c-1.35-1.338-1.352-3.506,0-4.846l19.54-19.148c1.352-1.338,3.543-1.338,4.895,0l19.539,19.148c1.352,1.34,1.352,3.506,0,4.846c-1.352,1.338-3.541,1.338-4.893,0L23,19.295L5.906,34.998z</strong></li>
                <li>iconViewBox - Default value <strong>0 0 46.001 46.001</strong></li>
                <li>fillColor - Default value <strong>#42b983</strong></li>
            </ol>
        </p>
        <div class="card-text">
            <ScrollToTop />
        </div>
    </div>
    <footer class="nugget-demo-footer-container">
      <Grid :columns="1">
        <GridItem class="nugget-grid-item-default">
          Created with ❤️ using <a class="vue-link" href="https://vuejs.org/">VueJs</a> by Shreerang Patwardhan.
        </GridItem>
        <GridItem class="nugget-grid-item-default">
          <a href="https://twitter.com/shreerangp" class="footer-social-link">
            <svg fill="#fff" height="24" width="24" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Follow me on Twitter</title><path d="M23.954 4.569c-.885.389-1.83.654-2.825.775 1.014-.611 1.794-1.574 2.163-2.723-.951.555-2.005.959-3.127 1.184-.896-.959-2.173-1.559-3.591-1.559-2.717 0-4.92 2.203-4.92 4.917 0 .39.045.765.127 1.124C7.691 8.094 4.066 6.13 1.64 3.161c-.427.722-.666 1.561-.666 2.475 0 1.71.87 3.213 2.188 4.096-.807-.026-1.566-.248-2.228-.616v.061c0 2.385 1.693 4.374 3.946 4.827-.413.111-.849.171-1.296.171-.314 0-.615-.03-.916-.086.631 1.953 2.445 3.377 4.604 3.417-1.68 1.319-3.809 2.105-6.102 2.105-.39 0-.779-.023-1.17-.067 2.189 1.394 4.768 2.209 7.557 2.209 9.054 0 13.999-7.496 13.999-13.986 0-.209 0-.42-.015-.63.961-.689 1.8-1.56 2.46-2.548l-.047-.02z"/></svg>
          </a>
          <a href="https://www.reddit.com/user/shreerangp" class="footer-social-link">
            <svg fill="#fff" height="24" width="24" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Follow me on Reddit</title><path d="M2.204 14.049c-.06.276-.091.56-.091.847 0 3.443 4.402 6.249 9.814 6.249 5.41 0 9.812-2.804 9.812-6.249 0-.274-.029-.546-.082-.809l-.015-.032c-.021-.055-.029-.11-.029-.165-.302-1.175-1.117-2.241-2.296-3.103-.045-.016-.088-.039-.126-.07-.026-.02-.045-.042-.067-.064-1.792-1.234-4.356-2.008-7.196-2.008-2.815 0-5.354.759-7.146 1.971-.014.018-.029.033-.049.049-.039.033-.084.06-.13.075-1.206.862-2.042 1.937-2.354 3.123 0 .058-.014.114-.037.171l-.008.015zm9.773 5.441c-1.794 0-3.057-.389-3.863-1.197-.173-.174-.173-.457 0-.632.176-.165.46-.165.635 0 .63.629 1.685.943 3.228.943 1.542 0 2.591-.3 3.219-.929.165-.164.45-.164.629 0 .165.18.165.465 0 .645-.809.808-2.065 1.198-3.862 1.198l.014-.028zm-3.606-7.573c-.914 0-1.677.765-1.677 1.677 0 .91.763 1.65 1.677 1.65s1.651-.74 1.651-1.65c0-.912-.739-1.677-1.651-1.677zm7.233 0c-.914 0-1.678.765-1.678 1.677 0 .91.764 1.65 1.678 1.65s1.651-.74 1.651-1.65c0-.912-.739-1.677-1.651-1.677zm4.548-1.595c1.037.833 1.8 1.821 2.189 2.904.45-.336.719-.864.719-1.449 0-1.002-.815-1.816-1.818-1.816-.399 0-.778.129-1.09.363v-.002zM2.711 9.963c-1.003 0-1.817.816-1.817 1.818 0 .543.239 1.048.644 1.389.401-1.079 1.172-2.053 2.213-2.876-.302-.21-.663-.329-1.039-.329v-.002zm9.217 12.079c-5.906 0-10.709-3.205-10.709-7.142 0-.275.023-.544.068-.809C.494 13.598 0 12.729 0 11.777c0-1.496 1.227-2.713 2.725-2.713.674 0 1.303.246 1.797.682 1.856-1.191 4.357-1.941 7.112-1.992l1.812-5.524.404.095s.016 0 .016.002l4.223.993c.344-.798 1.138-1.36 2.065-1.36 1.229 0 2.231 1.004 2.231 2.234 0 1.232-1.003 2.234-2.231 2.234s-2.23-1.004-2.23-2.23l-3.851-.912-1.467 4.477c2.65.105 5.047.854 6.844 2.021.494-.464 1.144-.719 1.833-.719 1.498 0 2.718 1.213 2.718 2.711 0 .987-.54 1.886-1.378 2.365.029.255.059.494.059.749-.015 3.938-4.806 7.143-10.72 7.143l-.034.009zm8.179-19.187c-.74 0-1.34.599-1.34 1.338 0 .738.6 1.34 1.34 1.34.732 0 1.33-.6 1.33-1.334 0-.733-.598-1.332-1.347-1.332l.017-.012z"/></svg>
          </a>
          <a href="https://www.linkedin.com/in/shreerangp/" class="footer-social-link">
            <svg fill="#fff" height="24" width="24" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Add me to LinkedIn</title><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          </a>
          <a href="https://shreerangpatwardhan.blogspot.com/" class="footer-social-link">
            <svg fill="#fff" height="24" width="24" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Latest posts on Blogger</title><path d="M21.976 24H2.026C.9 24 0 23.1 0 21.976V2.026C0 .9.9 0 2.025 0H22.05C23.1 0 24 .9 24 2.025v19.95C24 23.1 23.1 24 21.976 24zM12 3.975H9c-2.775 0-5.025 2.25-5.025 5.025v6c0 2.774 2.25 5.024 5.025 5.024h6c2.774 0 5.024-2.25 5.024-5.024v-3.975c0-.6-.45-1.05-1.05-1.05H18c-.524 0-.976-.45-.976-.976 0-2.776-2.25-5.026-5.024-5.026zm3.074 12H9c-.525 0-.975-.45-.975-.975s.45-.976.975-.976h6.074c.526 0 .977.45.977.976s-.45.976-.975.976zm-2.55-7.95c.527 0 .976.45.976.975s-.45.975-.975.975h-3.6c-.525 0-.976-.45-.976-.975s.45-.975.975-.975h3.6z"/></svg>
          </a>
          <a href="https://ko-fi.com/shreerangp" class="footer-social-link">
            <svg fill="#fff" height="24" width="24" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>Buy me a Ko-fi</title><path d="M23.881 8.948c-.773-4.085-4.859-4.593-4.859-4.593H.723c-.604 0-.679.798-.679.798s-.082 7.324-.022 11.822c.164 2.424 2.586 2.672 2.586 2.672s8.267-.023 11.966-.049c2.438-.426 2.683-2.566 2.658-3.734 4.352.24 7.422-2.831 6.649-6.916zm-11.062 3.511c-1.246 1.453-4.011 3.976-4.011 3.976s-.121.119-.31.023c-.076-.057-.108-.09-.108-.09-.443-.441-3.368-3.049-4.034-3.954-.709-.965-1.041-2.7-.091-3.71.951-1.01 3.005-1.086 4.363.407 0 0 1.565-1.782 3.468-.963 1.904.82 1.832 3.011.723 4.311zm6.173.478c-.928.116-1.682.028-1.682.028V7.284h1.77s1.971.551 1.971 2.638c0 1.913-.985 2.667-2.059 3.015z"/></svg>
          </a>
        </GridItem>
        <GridItem class="nugget-grid-item-default">
           If you love my content and want me to keep building this library 👨‍💻
           <a class="button" href="https://ko-fi.com/shreerangp">
             <h2>Buy me ☕️</h2>
           </a>
        </GridItem>
      </Grid>
    </footer>
  </div>
</template>

<script>
const swatchImg = require('./assets/color_swatch.jpeg');
import { QuantitySelector, StarRating, Grid, GridItem, Alert, BagCount, VarianceSelector, ScrollToTop } from 'ecommerce-ui-nuggets';

export default {
	name: 'app',
	components: {
		QuantitySelector,
		StarRating,
		Grid,
		GridItem,
		Alert,
    BagCount,
    VarianceSelector,
    ScrollToTop
	},
	data() {
		return {
			gridData: [
				{ rating: 2.4 },
				{ rating: 3.5 },
				{ rating: 1.9 },
				{ rating: 4.4 },
				{ rating: 3.7 },
				{ rating: 2.4 },
				{ rating: 3.5 },
				{ rating: 1.9 },
			],
			errorActive: false,
			warnActive: false,
			inlineErrorActive: false,
			inlineWarnActive: false,
			sizeSelectorData: [
				{ name: 'Xtra Small', value: 'XS' },
				{ name: 'Small', value: 'S', availability: false },
				{ name: 'Medium', value: 'M', availability: false },
				{ name: 'Large', value: 'L' },
				{ name: 'Xtra Large', value: 'XL' },
				{ name: 'Double XL', value: 'XLL' },
			],
			colorSelectorData: [
				{ name: 'Black/Red', value: 'XS', image: { background: swatchImg, position: '-0px 0' } },
				{
					name: 'Black/Pink',
					value: 'S',
					availability: false,
					image: { background: swatchImg, position: '-56px 0' },
				},
				{
					name: 'Black/Tan',
					value: 'M',
					availability: false,
					image: { background: swatchImg, position: '-112px 0' },
				},
				{ name: 'Black/Tan/Purple', value: 'L', image: { background: swatchImg, position: '-168px 0' } },
				{ name: 'Magnta Multi', value: 'XL', image: { background: swatchImg, position: '-224px 0' } },
			],
			quantitySelectorData: [
				{ name: '100 Sheets', value: '100' },
				{ name: '200 Sheets', value: '200' },
				{ name: '350 Sheets', value: '350' },
				{ name: '500 Sheets', value: '500' },
			],
      singleSizeData: [{ name: 'Xtra Large', value: 'XL' }],
      getCountVal: '',
      getVariantVal: ''
		};
	},
	methods: {
    passCountVal: function(val) {
      this.getCountVal = val
    },
    passVariantVal: function(val) {
      this.getVariantVal = val
    },
		setActive: function() {
			if (this.errorActive === true) {
				this.errorActive = false;
			} else {
				this.errorActive = true;
			}
		},
		setWarnActive: function() {
			if (this.warnActive === true) {
				this.warnActive = false;
			} else {
				this.warnActive = true;
			}
		},
		setInlineErrorActive: function() {
			if (this.inlineErrorActive === true) {
				this.inlineErrorActive = false;
			} else {
				this.inlineErrorActive = true;
			}
		},
		setInlineWarnActive: function() {
			if (this.inlineWarnActive === true) {
				this.inlineWarnActive = false;
			} else {
				this.inlineWarnActive = true;
			}
		},
	},
};
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	padding: 10px;
}
.card {
	border: solid 1px #ccc;
	border-radius: 5px;
	padding: 10px;
	text-align: center;
	margin: 10px;
}
.card-text {
	text-align: left;
}
img {
	width: 50%;
}
@media all and (max-width: 1000px) {
	img {
		width: 70%;
	}
}
.nugget-grid-item {
	border: dashed 1px #ccc;
}

.nugget-grid-item-default {
	border: none;
  padding: 5px;
}

.nugget-grid-item > .nugget-stars {
	width: 100%;
}

button {
	padding: 10px;
	border-radius: 5px;
}

strong {
	word-break: break-all;
    color: rgb(27, 149, 224);
}

.compo-label {
  margin: 10px 0;
}

h1, .highlight-text {
  color: #42b983;
}

.default-color {
  color: #000;
}

.nugget-demo-footer-container {
  padding: 1.5em;
  background-color: #000;
  color: #fff;
}

.nugget-demo-footer-container .button h2 {
  margin: 0px;
}

.footer-social-link {
  padding: 2px 7px;
}

.button {
  color: #fff;
  padding: 7px;
  text-decoration: none;
  border: solid 1px #fff;
  border-radius: 5px;
  display: inline-block;
}

.vue-link {
  color: #42b983;
  text-decoration: none;
}
</style>
