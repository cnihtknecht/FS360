<template>
    <div class="
                flex
                flex-col
                w-56
                transition-all
                duration-500
                ease-in-out
                bg-gray-800
                h-screen
                shadow-2xl
                pt-16
                ">
        <menuLink
            :url="'/dashboard'"
            :class="{
                'text-gray-500':!$route.path.includes('/dashboard'),   //when the current path is not /dashboard, set gray text
                'text-white':$route.path.includes('/dashboard'),       //when current path is /dashboard,  set white text in the link
                'hover:bg-gray-600':true,
                'hover:text-white':true  
                }">
            <template v-slot:icon-word>
                <div class="flex items-center justify-start overflow-x-hidden">   <!--overflow-x-hidden will hide the div when the text overflows-->
                    <i class="fas fa-home l-6 mr-4"> </i>
                    <label class="flex-shrink-0 ml-2 text-sm font-sans
                    tracking-wide cursor-pointer">                               <!--flex-shrink-0 will mean the text will not wrap-down, fixed size, it will overflow. This in combo with the hide when x-axis overflow before this-->
                                                                                 <!-- cursor-pointer will change the cursor when mouse is over this div-->                      
                        Dashboard </label>
                </div>
            </template>
        </menuLink>

        <menuLinkList :url="'/products'"
            :class="{
                'text-gray-500':!$route.path.includes('/products'), 
                'text-white':$route.path.includes('/products'),
                'cursor-pointer':true
            }">
            <template v-slot:icon-word>
                <div class="flex items-center justify-start overflow-x-hidden hover:text-white">
                    <i class="fas fa-truck-loading ml-6 mr-4"></i>
                    <label class="flex-shrink-0 ml-2 text-sm font-sans
                    tracking-wide cursor-pointer">
                        Products</label>
                </div>        
            </template>
            <template v-slot:sub-link>
                <menuLink
                    :url="'/products/new'"
                    :class="{
                        'text-gray-500':!$route.path.includes('/products/new'),
                        'text-white':$route.path.includes('/products/new'),
                        'hover:text-white':true,
                        'cursor-pointer':true
                    }">
                    <template v-slot:icon-word>
                        <div class="flex items-center justify-start overflow-hidden py-2">
                            <i class="fas fa-coffee ml-6 mr-4"></i>
                            <label class="flex-shrink-0 ml-2 text-sm font-sans tracking-wide cursor-pointer">
                                New Product </label>
                        </div>
                    </template>                                
                </menuLink>
            </template>
            
        </menuLinkList>    


    </div>
</template>
<script>
    import MenuLink from "~/components/items/MenuLink.vue";
    import MenuLinkList from "~/components/items/MenuLinkList.vue";

export default {
    components:{
        MenuLink,
        MenuLinkList
    }
    
}
</script>