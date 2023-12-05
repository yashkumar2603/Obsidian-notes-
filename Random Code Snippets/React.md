```JavaScript
<TextLoop>
	I am a
		<Span>
			<Typewriter
				options={{
					strings: Bio.roles,
					autoStart: true,
					deleteSpeed: 60,
					delay: 5,
					loop: true,
				}}/>
		</Span>
</TextLoop>
```
To create a typewriter loop typing stuff.
```JavaScript
export const Bio = {
  name: "Yash Kumar",
  roles: [
    "Full Stack Developer",
    "Android Developer",
    "UI/UX Designer",
    "Programmer",
  ],
};
```
Sample Bio piece in constants,js