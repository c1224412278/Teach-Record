tree 實作
====================

```
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>
        <p> (You can double click on an item to turn it into a folder.) </p>
        <div id="app">
            <item :model='treeData'></item>
        </div>
    </body>
    <template id="item-template">
        <div>
            <ul>
                <div v-on:click="toggle">
                    {{ model.name }}
                    <span v-if="IsChildren()"> {{ isOpen ? '-' : '+' }}</span>
                </div>

                <div v-show="isOpen">
                    <item v-for="model in model.children" :model="model"></item>
                </div>
            </ul>
        </div>
    </template>
    <script>
    var data = {
        name: 'My Tree',
        children: [
            { name: 'hello' },
            { name: 'wat' },
            {
            name: 'child folder',
            children: [
                {
                name: 'child folder',
                children: [
                    { name: 'hello' },
                    { name: 'wat' }
                ]
                },
                { name: 'hello' },
                { name: 'wat' },
                {
                name: 'child folder',
                children: [
                    { name: 'hello' },
                    { name: 'wat' }
                ]
                }
            ]
            }
        ]
    }

    Vue.component('item', {
        template:'#item-template' , 
        props:{
            model : Object ,
        },
        data(){
            return{
                isOpen:false,
                IsChildren()
                {
                    if(this.model.children == null)
                    {
                        return false;
                    }
                    else return true;
                }
            }
        },
        methods: {
            toggle()
            {
                this.isOpen = !this.isOpen
            } , 
        },
    })

    var app = new Vue({
        el:"#app" ,
        data(){
            return{
                treeData: data
            }
        }
    })
    </script>
</html>
```
