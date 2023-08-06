# Django-Authentication


1. import   "from django.contrib.auth import logout  , authenticate , login"  ---------- > for login in and log out in page


2. first authanticate (using authanticate method) username and password from values submitted by user.

3. for authantication of values

   if user values are not none then login the user using (login function) and redirect user to desired page. otherwise redirect the user to the login page again.
 
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



4.for home page :
             
            i) if user is anonymous then render the login page to user. otherwise render content template to user.

       Example: 
                      
                        def index (request):
    if request.user.is_anonymous:
        return render(request , 'login.html')

    return render(request , 'index.html') 

5. for logout 

   if user want to logout from  page the logout the session using (logout function)

   Example: 
          def logout_user(request):

              logout(request )

          return redirect('/login')
