# Notes

*errors & solutions*
=============================
**Problem**: Input type (__int64) and bias type (float) should be the same

**Solution**: I think the general idea is that nothing can be an int? Seems a little weird. Perhaps the framework isn't capable of rounding, so let's go with float. Solution is 
return torch.tensor([float(x) for x in vector]), torch.tensor(from_square), torch.tensor(to_square)
