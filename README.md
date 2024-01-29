function segmentElement(element):
begin
if element is null then
return [empty list]
if All child nodes of element are not included in ignoreElements then
if All child nodes of element are TEXT NODE or included in inlineElements then
text ← text content of element ;
if text is not null then
return [text]
childNodes ← child nodes of element ;
texts ← [empty list] ;
for i = 0 to |childNodes| do
child ← childNodes[i];
nodeT ype ← node type of child;
if nodeT ype = TEXT NODE then
textContent ← text content of child ;
if textContent 6= null then
Append textContent to texts ;
tagN ame ← tag name of child ;
if (tagN ame = null) OR (tagN ame ∈ ignoreElements) then
continue;
if tagN ame ∈ blockElements then
childT exts ← segmentElements(child) ;
Concatenate texts with childT exts ;
if tagN ame is included in inlineElements then
textContent ← text content of child ;
if textContent 6= null then
Append textContent to texts
return texts
end
