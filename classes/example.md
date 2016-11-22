# Class Construction Example

<div class="spec es6">ES6</div>

This is a complete example of a simple counter web app. We create a View, Model and extended view to emulate a basic MVC framework (like Backbone).

```javascript
function TemplateEngine(tpl, data) {
    var re = /<%([^%>]+)?%>/g, match;
    while(match = re.exec(tpl)) {
        tpl = tpl.replace(match[0], data[match[1].trim()])
    }
    return tpl;
}

class View {

    constructor(options) {
        this.model = options.model;
        this.template = options.template;
    }

    render() {
        return TemplateEngine(this.template, this.model.toJSON());
    }

}

class Model {

    constructor(properties) {
        Model.count++;
        this.properties = properties;
    }

    static count = 0;

    toJSON() {
        return this.properties;
    }

}

class ExpireView extends View {

    constructor(options) {
        super(options);
        this.count = options.count;
    }

    countdown() {
        this.interval = setInterval(()=>{
            if(this.count === 0) {
                return clearInterval(this.interval);
            }
            this.render();
            this.count--;
        },1000)
    }

    render() {
        const compiled = super.render();
        console.log(`${compiled} (${this.count})`);
    }

}
```

We can then invoke our countdown web app.

```javascript

const don = new Model({
    name : 'don'
});

const john = new Model({
    name : 'john'
});

console.log(Model.count); //2

const view = new View({
    model: callum,
    template: 'Hello, my name is <% name %>'
});

console.log(view.render()); //Hello, my name is callum

const expireView = new ExpireView({
    model: john,
    template: 'Hello, my name is <% name %>',
    count : 10
});

expireView.countdown(); //Hello, my name is john (10)...

```
