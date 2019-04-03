# Angular Mentions - Francis fork

Forked from [https://github.com/francisvgi/fvi-angular-mentions](https://github.com/dmacfarlane/angular-mentions)

Forked from [dmacfarlane/angular-mentions](https://github.com/dmacfarlane/angular-mentions)

Forked from [dessalines/angular-mentions](https://github.com/dessalines/angular-mentions)

Angular mentions inspired by [Ment.io](https://github.com/jeff-collins/ment.io).

Provides auto-complete suggestions for @mentions in text input fields, text areas,
and content editable fields. Not fully browser tested and comes without warranty!

git clone https://github.com/israelor6/fvi-angular-mentions
cd angular-mentions
ng serve

### Usage

Add the package as a dependency to your project using:

    npm install --save fvi-angular-mentions

Add the CSS to your index.html:

    <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">

Add the module to your app.module imports:

    import { MentionModule } from 'fvi-angular-mentions/mention';
    ...

    @NgModule({
        imports: [ MentionModule ],
        ...
    })

Add the `[mentions]` directive to your input element:

    <input type="text" [mentions]="mentionItems">

Where `mentionItems` is an an array of `MentionItem`:

```
mentionItems: Array<MentionItem> = [
    {
      items: {"jerry", "ben", "tom"},
      triggerChar: '@',
	  mentionSelect: formatMention
    },
    {
      items: {"happy", "sad", "trending"},
      triggerChar: '#',
    },
    {
      items: [
        {
          id: 1,
          name: "community_A"
        },
        {
          id: 2,
          name: "community_B"
        }
      ],
      labelKey: "name",
      triggerChar: "~"
    }
  ];
```

#### Configuration Options

```
export interface MentionItem {

  // The list of items to be searched on.
  items: Array<{}>;

  // the character that will trigger the menu behavior
  triggerChar: string;

  // option to specify the field in the objects to be used as the item label
  labelKey?: string;

  // option to limit the number of items shown in the pop-up menu
  maxItems?: number;

  // option to diable internal filtering. can be used to show the full list returned
  // from an async operation (or allows a custom filter function to be used - in future)
  disableSearch?: boolean;

  // template to use for rendering list items
  mentionListTemplate?: TemplateRef<any>;

  // internal use
  searchList? : MentionListComponent;
  
  // optional function to format the selected item before inserting the text
  selectMention? : any;
  
  // option to open the dropdown upward
  upwad? boolean;
}
```


#### Output Events

- `(searchTerm)=""` event emitted whenever the search term changes. Can be used to trigger async search.

- `(selectedTerm)=""` event emitted whenever a term is selected.

THANKS TO DESSALINES (https://github.com/dessalines/angular-mentions) AND DMACFARLANE(https://github.com/dmacfarlane/angular-mentions).

