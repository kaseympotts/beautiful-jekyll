
body { 
 margin-right: auto; 
 margin-left: auto; 
 width: 800px; 
 padding-top: 50px;
 padding-left: 10px;
 padding-bottom: 50px;
 padding-right: 10px;
 background-color: oldlace;
}



header { 
  background-color: black; 
  height: 60px;
  padding: 40px 0px 0px 20px;
} 
  
#site-title {
  font-size: 120%;
  text-transform: uppercase;
  margin: 0px 30px 0px 0px;
}
  
.navbar a {
  color: white;
  margin: 0px 15px 0px 0px;
  font-family: Verdana,sans-serif;
  font-size: 15px;
  text-decoration: none;
  line-height: 1.65;
}
  
.navbar i {
  color: white;
}


footer {
  color:white;
  height: 1100px;
  background-color: #696969;
  padding-top: 50px;
  font-family: Verdana,sans-serif;
  font-size: 15px;
  line-height: 1.65;
  text-decoration: none;
  text-align: center;
}
  
footer a {
  color: orange;
}

.footer-list {
	display: block;
	text-align: left;
	margin-left: 80px;
	}
	
pre{
  font-family: Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
  margin-bottom: 5px;
  padding: 5px;
  background-color: #eee;
  width: 750px!ie7;
  padding-bottom: 10px!ie7;
  color: black;
  text-align: left;
	
}

###
    ###  LAYOUT INHERITANCE
    ###
    ###  pages built by adding elements 
    ###  to other page layouts 
    ###

          default.html layout 
          │
          └── nice-text.html layout 
              │
              └── liquid-table.html layout
                  # see liquid table below



          ###
          ###  default.html layout
          ###

          <html>
          <head>
            <body>                                
              <header>   

              {{ content }}     

              <footer>           
            </body>  
          </html>     

       

          ---
          layout: default
          ---

          <div class="pretty-text">

          <h1> {{ page.title }} </h1>

          {{ content }}

          </div>


          ###
          ### liquid-table.html layout
          ###

          ---
          layout: default
          ---

          {{ content }}

          #  liquid table starts here

        ---
        layout: liquid-table
        title: 'amiright?'
        reynolds:
          strengths:
          - good father
          - funny
          - dated alanis morissette
          weaknesses: 
          - singing
          - green lantern movie
          - tennis backhand 
        gosling:
          strengths: 
          - builds houses
          - is a real boy
          - never dated alanis morissette
          weaknesses: 
          - micky mouse club
          - cries a lot
          - not ryan reynolds
        ---


        <h2> Ryan vs Ryan </h2>

        <table id="ryan-v-ryan">

        <thead>
          <tr>
            <th>  <h3>  Ryan Reynolds  </h3>  </th>
            <th>  <h3>  Ryan Gosling  </h3>  </th>
          </tr>
        </thead>

        <tbody>
        <tr>
          <td>
            <h4>  Strengths  </h4>
            <ul>

              ###  LIQUID LOOPS WITH YAML DATA
              ###  reynolds:
              ###    strengths:
              ###    - good father
              ###    - funny
              ###    - dated alanis morissette

              {% for item in page.reynolds.strengths %}
                 <li>  {{ item }}  </li>
              {% endfor %}

              ###    LIQUID LOOP CREATES HTML CODES:
              ###    <li> good father </li>
              ###    <li> funny </li>
              ###    <li> dated alanis morissette </li>        

            </ul>
            <br>
            <h4>  Weaknessess  </h4>
            <ul>

              {% for item in page.reynolds.weaknesses %}
                 <li>  {{ item }}  </li>
              {% endfor %}

            </ul>  
          </td>
          <td>
            <h4>  Strengths  </h4>
            <ul>

              {% for item in page.gosling.strengths %}
                <li>  {{ item }}  </li>
              {% endfor %}

            </ul>
            <br>
            <h4>  Weaknessess  </h4>
            <ul>

              {% for item in page.gosling.weaknesses %}
                 <li>  {{ item }}  </li>
              {% endfor %}

            </ul>
          </td>
        </tr> 
        </table>


page footer


      ###  PAGE CONSTRUCTION WITH LIQUID
 
      ###
      ###  default.html layout
      ###
      
           <html>
           {% include head.html %}
	     <body>   

	       {% include header.html %}   

	       {{ content }}     

	       {% include footer.html %}   

	     </body>  
           </html>     

      ###
      ###  {% include xxxx.html %}
      ###  is replaced by content
      ###  from the file xxxx.html
      ###  in the _includes folder.
      ### 
      
      ###  {% include xxxx.html %} Files: 

       >>  head.html
       >>  header.html
       >>  footer.html
