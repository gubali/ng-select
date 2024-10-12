# ng-select
with all select and show count 

# template


<ng-select
  [items]="people"
  [multiple]="true"
  bindLabel="label"
  [selectableGroup]="true"
  [closeOnSelect]="false"
  bindValue="value"
  groupBy="selectedAllGroup"
  [selectableGroup]="true"
  [selectableGroupAsModel]="false"
  [(ngModel)]="selectedPeople"
>
  <ng-template
    ng-optgroup-tmp
    let-item="item"
    let-item$="item$"
    let-index="index"
  >
    <input id="item-{{ index }}" type="checkbox" [ngModel]="item$.selected" />
    Select All
  </ng-template>
  <ng-template
    ng-option-tmp
    let-item="item"
    let-item$="item$"
    let-index="index"
  >
    <input id="item-{{ index }}" type="checkbox" [ngModel]="item$.selected" />
    {{ item.label }}
  </ng-template>
  <ng-template ng-multi-label-tmp let-items="items" let-clear="clear">
    @for (item of items | slice: 0 : 2; track item) {
    <div class="ng-value">
      <span class="ng-value-label"> {{ item.label }}</span>
      <span class="ng-value-icon right" (click)="clear(item)" aria-hidden="true"
        >×</span
      >
    </div>
    } @if (items.length > 2) {
    <div class="ng-value">
      <span class="ng-value-label">{{ items.length - 2 }} more...</span>
    </div>
    }
  </ng-template>
</ng-select>
ssssss

====================================type script======================

  people: any[] = [];
  selectedPeople = [];
  ngOnInit() {
    this.people = [
      { label: 'Vilnius', value: 'Vilnius' },
      { label: 'Kaunas', value: 'Kaunas' },
      { label: 'Pavilnys', value: 'Pavilnys' },
      { label: 'Vilnius', value: 'Vilnius' },
    ];
    this.selectedPeople = [this.people[0].label, this.people[1].label];
    this.selectAllForDropdownItems(this.people);
    console.log('selected people', this.selectedPeople);
  }
  selectAllForDropdownItems(items: any[]) {
    let allSelect = (items) => {
      items.forEach((element) => {
        element['selectedAllGroup'] = 'selectedAllGroup';
      });
    };

    allSelect(items);
  }
