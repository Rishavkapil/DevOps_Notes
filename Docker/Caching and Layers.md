
FROM node:20-alpine               **-> Layer 1** 

WORKDIR /usr/src/app             **-> Layer 2**

COPY . .                                     **-> Layer 3** 

RUN npm install                        **-> Layer 4** 
	


EXPOSE 3000

CMD ["node", "testing.js"]





**Why do docker need layering ?**


1. **Layering for build caching**  : 
			Each command in docker file (RUN, COPY, ADD etc ) creates a separate layer. 
			Docker caches these layers, so when you  rebuild an image , it reuses unchanged layers instead of redoing everything from scratch . 

2. **Layer reuse (efficiency across images ) :**  
			Docker layers are shared between images . 
			if you have multiple images using **node:20-alpine** , docker only download it once and reuses it across all images. 
3. **Faster Build time**



IF any Layer changes all the layers below that layer will also be changed and cannot be cached
