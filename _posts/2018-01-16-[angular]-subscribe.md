# subscribe

```typescript
res:any = {
    downloadUrl:'',
    version:''
  }

  ionViewDidLoad(){
    this.api.get('/versions/versionCheck',{deviceType:'android',version:this.version}).subscribe(Response=>{
      this.res = Response;
      if(this.res.version == 'same'){
        return;
      }else{
        const browser = this.iab.create(this.res.downloadUrl);
        browser.show();
      }
    });
  }
```

res객체를 미리 만들어놓지 않으면 this.res.version의 version에 대해 받아들이지 못한다.