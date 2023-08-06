# Django-Authentication


### 1. Import   "from django.contrib.auth import logout, authenticate, login"   (for  making login and logout in page).


### 2. First, authenticate (using the 'authenticate' method) the username and password from values submitted by the user. If username and password are correct then this function will returns the user object , otherwise it will returns None .

### 3. For login the user

   If the user is not none ( username and password are correct ) then login the user using (login function) and redirect the user to the desired page. Otherwise, redirect the user to the login page again.
 
Example:  
          
    def login_user(request):
       if request.method=="POST":
          username=request.POST.get('username')
          passwd=request.POST.get('password')
          user=authenticate(username=username , password=passwd)
          if user is not None:
             login(request , user)
             return redirect('/')
          else:
             return render(request ,  'login.html')
        return render(request ,  'login.html')



### 4. For the home page :
             
  If the user is anonymous then render the login page to the user. otherwise, render the content template to the user.

   Example: 
                      
     def index (request):
        if request.user.is_anonymous:
           return render(request , 'login.html')
        return render(request , 'index.html') 

### 5. For logout 

   If user wants to logout from  the page the logout the session using (logout function)

   Example: 

           def logout_user(request):
              logout(request )
              return redirect('/login')
