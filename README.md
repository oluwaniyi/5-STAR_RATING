# STAR_RATING
To easily create star-rating ranging from 0.00 to 5.00 with just a single line command. 
/* Documentation
				create_star_rating(full_color, empty_color, rating, star_id, background_color)
				The create_star_rating function requires:
				full_color        :  The color for full star rating
				empty_color       :  The color for empty star rating
				rating            :  The rating which ranges from 0.00 - 5.00
				star_id           :  The "id" of the element where rating will be inserted 
				background_color  :  The background_color of the star which preferrably should match that of the parent element.
			*/

			/*example*/
			create_star_rating('#a0c8ff', '#ffffff', 5.00, 'html-rate', "#383737");
			create_star_rating('#a0c8ff', '#ffffff', 2.30, 'css-rate', "#383737");
			create_star_rating('#a0c8ff', '#ffffff', 3.60, 'php-rate', "#383737");
			create_star_rating('#a0c8ff', '#ffffff', 4.80, 'javascript-rate', "#383737");

			/*The function that creates the star_rating*/
			function create_star_rating(full_color, empty_color, rating, star_id, background_color){
			let remaining = 5 - Math.ceil(rating);
			let full_star = Math.floor(rating);
			let fraction =  Math.round(((rating - Math.floor(rating))*100),2);
			let star_string = "";
			let fraction_css = "background: linear-gradient(90deg, "+full_color+" "+fraction+"%,"+empty_color+" "+fraction+"%); color:"+background_color+";";
			let whole_css = "background: "+full_color+";color:"+background_color+";";
			let not_filled = "background: "+empty_color+";color:"+background_color+";"; 
			for (var i = 1; i < Math.ceil(rating)+1; i++) {
				if(i <= full_star){
					star_string = star_string+'<i class="fas fa-star" data-fa-transform="shrik-1" data-fa-mask="fas fa-square-full" style="'+whole_css+'"></i>'; 
				}
				else{
					star_string = star_string + '<i class="fas fa-star" data-fa-transform="shrik-1" data-fa-mask="fas fa-square-full" style="'+fraction_css+'"></i>'
				}
			}
			for (var i = 0; i < remaining; i++) {
				star_string = star_string+'<i class="fas fa-star" data-fa-transform="shrik-1" data-fa-mask="fas fa-square-full" style="'+not_filled+'"></i>'; 
			}

			document.getElementById(star_id).innerHTML = star_string;
		}
		
