<template>
  <div class="hello">
    <button @click="compare">cancel</button>
    <button @click="setObjCookie">Set Object to Cookie</button>
    <button @click="getCookie">Get Cookie Content</button>
  </div>
</template>

<script>

//    function setCookie(name,value) {
//     document.cookie = name + "=" + (value || "")  + "; path=/";
// }
 
// function delete_cookie(name) {
//   document.cookie = [name, '=; expires=Thu, 01-Jan-1970 00:00:01 GMT; path=/; domain=.', window.location.host.toString()].join('');
// }

var person = { name:'Rudssss', age: 10, color:'black'}; //mock up object in local
var returnItem = getCookie("personDetails"); // specifies the object in cookie

function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];
        while (c.charAt(0)==' ') c = c.substring(1,c.length);
        if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
}


export default {
  // data() {
  //   return {
  //         person : { name:'joe', age: 7, color:'green'}
  //     }
  //   },
  methods: {
    compare() {
        console.log(JSON.stringify(person) + "---person from local");
        console.log(returnItem + "---person from cookie");

        if(JSON.stringify(person) === returnItem) {
          console.log("no changes, DON'T show modal");
        } else {
          console.log("changes made, SHOW modal");
        }
    },

    setObjCookie() {
      let a = JSON.stringify(person);
      this.setCookie("personDetails", a);
      console.log(a);
    },

    setCookie(name,value) {
        document.cookie = name + "=" + (value || "")  + "; path=/";
    },

    // getCookie(name) {
    //     var nameEQ = name + "=";
    //     var ca = document.cookie.split(';');
    //     for(var i=0;i < ca.length;i++) {
    //         var c = ca[i];
    //         while (c.charAt(0)==' ') c = c.substring(1,c.length);
    //         if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    //     }
    //     return null;
    // },
    
    getCookie() {
        console.log(document.cookie);
    },

    delete_cookie(name) {
      document.cookie = [name, '=; expires=Thu, 01-Jan-1970 00:00:01 GMT; path=/; domain=.', window.location.host.toString()].join('');
    }
    

  }
}

</script>

