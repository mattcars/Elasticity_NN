# Elasticity_NN

This project looks at a material microstructure created by 2 different materials. Material 1 and Material 2 have different Young's Moduli and different poisson's ratio. These materials are then arranged randomly in one 5x5 quadrant of the material, which is then reflected across each axis to create a full 10x10 material sample. 

The Regression notebook creates an architecture for a neural network that can analyze the 5x5 material structure (in terms of 1's and 0's to represent each material) and attempt to predict the net Young's Modulus of the entire sample. This Young's Modulus is solved by applying a force across one end of the sample and fixing the other end. By taking the ratio of force / displacement, the net Young's Modulus is calculated. This is done on a number of samples which is then fed into the regression network to train. The regression network replaces the finite element analysis step, speeding up computation. 

The Generativve Adversarial Network attempts to create a network that can take a Young's Modulus and create a material microstructure that closely matches. 
This is done by creating a large sample of materials (5x5), then using those to train a Discriminator Network and then using a random noise vector for the Generator network. This is a conditional network so each network is also fed the expected Young's Modulus so that the GAN can take that as an input for generating random samples. 

The generated data is not evenly distributed which is reflected in the generated samples, which has trouble reproducing samples at higher modulus of elasticities. 
The generator seems to not have converged properly and works well creating samples around the 200-300 range, but not able to follow as the input modulus increases. 

This approach is based on research cited below where a similar GAN was created, but with different sample sizes. 

Citation: 
Mao, Y., He, Q., & Zhao, X. (2020). Designing complex architectured materials with generative adversarial networks. Science Advances, 6(17), eaaz4169. https://doi.org/10.1126/sciadv.aaz4169

# TODO
- Explore embedding in generator architecture to get more variety in samples
- explore literature for existing regression GAN structures
- Edit architecture so that the GAN can reach better results
