@library(shared-nishank@master) _

pipeline {
	agent {
		stage(test shared variables) {
			step {
				variables.test()
			}
		}
	}
}
				
