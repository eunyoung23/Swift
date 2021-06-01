- 스위프트 5.3에서부터 도입됨

```
//이전 버전에서는 
do {
  try parsing(data: [:])
} catch DataParsingError.missingRequiredField(let fieldName){

} catch let err as DataParsingError {
   switch err{
   case .invalidField .invalidType:
      //error handling code
      break
    default:
      break
   }
}

```

```
//스위프트 5.3버전에서는 
do {
  try parsing(data: [:])
} catch DataParsingError.invalidType, DataParsingError.invalidField {

} catch DataParsingError.missingRequiredField(let fieldName){

} catch {

}

```
