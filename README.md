**CGMLinearSolver**
This is a linear system solver that uses the CGM (Conjugate Gradient Method) to solve Ax=b problems. CGM iterates toward the correct value very quickly because it avoids computing Hessians and only moves in the direction of the conjugate. This includes a couple custom kernels for matrix-vector multiplication, vector operations, and a shared memory reducer. The main point of this approach is to optimize memory access and reduce computation, which makes it well suited for scientific computing and machine learning (gradient descent).

**MRIReconstructer**
MRI scans are often messy and unclear because they are non-Cartesian (the image data isn’t neatly organized in a cartesian coordinate system). I used a FHD (Fully-Hybrid Domain) algorithm to iteratively reconstruct the image and improve fidelity. This algorithm combines spatial and frequency domain techniques to produce a more accurate and sharp image while reducing memory footprint. 

**MRIReconstructerIO**
This one builds upon the previous implementation of the FHD algorithm to include real image reading and processing. This version takes an actual image, applies the previous reconstruction algorithm, and outputs the new image. Includes CUDA’s native I/O operations.
