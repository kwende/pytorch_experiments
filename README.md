# Notes

*errors & solutions*
=============================
**Problem**: Input type (__int64) and bias type (float) should be the same

**Solution**: I think the general idea is that nothing can be an int? Seems a little weird. Perhaps the framework isn't capable of rounding, so let's go with float. Solution is 
return torch.tensor([float(x) for x in vector]), torch.tensor(from_square), torch.tensor(to_square)
-------
**Problem**: Expected 3D (unbatched) or 4D (batched) input to conv2d, but got input of size: [100, 64]

**Solution**: nn.Conv2d expects an input in the shape [batch_size, channels, height, width]. Given groups=1, weight of size [64, 1, 2, 2], expected input[1, 100, 8, 8] to have 1 channels, but got 100 channels instead. 

The answer was to do "return np.reshape(torch.tensor([float(x) for x in vector]), (1,8,8)), torch.tensor(from_square), torch.tensor(to_square)", note the 1,8,8. The point is that there's 1 channel. 

