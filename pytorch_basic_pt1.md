# Pytorch Basic


## Two ways to build up a model

### Method 1

    class Net(torch.nn.Module):
	    def __init__(self,n_feature, n_hidden, n_output):
		    super(Net, self).__init__()
		    self.hidden = torch.nn.Linear(n_feature, n_hidden)
		    self.predict= torch.nn.Linear(n_hidden, n_output)
		def forward(self,x):
			x = F.relu(self.hidden(x))
			x = self.predict(x)
			return x

### Method 2

    net2 = torch.nn.Sequential(
    torch.nn.Linear(2,10),
    torch.nn.ReLU(),
    torch.nn.Linear(10,2),
    )

## Save model in two ways

torch.save(net1, 'net.pkl') # save entire net
torch.save(net1.state_dict(), 'net_params.pkl') # save only the parameters

## torch.randn

    v1 = torch.rand(2, 3) # Initialize with random number (uniform distribution)
    v2 = torch.randn(2, 3) # With normal distribution (SD=1, mean=0)

v1
tensor([[0.7403, 0.2839, 0.5947],
[0.5141, 0.6708, 0.5189]])

v2
tensor([[-1.7007, -1.3919, 0.9280],
[ 0.9036, -0.4951, 1.3435]])

## Tensor Operation

### torch.unsqueeze

    test_x = torch.unsqueeze(test_data.test_data, dim=1).type(torch.FloatTensor)[:2000]/255. # shape from (2000, 28, 28) to (2000, 1, 28, 28)
    
### torch.squeeze

t = torch.ones(2,1,2,1) _# Size 2x1x2x1_
r = torch.squeeze(t) _# Size 2x2_
r = torch.squeeze(t, 1) _# Squeeze dimension 1: Size 2x2x1_
    
### x.view(x.size(0), -1)

    w = w.view(w.size(0), -1) # flatten the output of conv2 to (batch_size, 32 * 7 * 7)

    x = torch.randn(2, 3) _# Size 2x3_
    y = x.view(6) _# Resize x to size 6_
    z = x.view(-1, 2) _# Size 3x2_

### fill_()

    v = torch.ones(3, 3); v[1].fill_(2) ;v[2].fill_(3)

tensor([[1., 1., 1.],
[2., 2., 2.],
[3., 3., 3.]])

### transpose()

    x = torch.randn(2, 3)
    tensor([[ 1.0028, -0.9893,  0.5809],
     [-0.1669,  0.7299,  0.4942]])
     
    torch.transpose(x, 0, 1)
    tensor([[ 1.0028, -0.1669],
     [-0.9893,  0.7299],
     [ 0.5809,  0.4942]])

### torch.mm()

    mat1 = torch.randn(2, 3)
    mat2 = torch.randn(3, 4)
    r = torch.mm(mat1, mat2)
    
    tensor([[ 1.0690, 1.7773, -0.2107, 2.9098],
    [ 2.2185, 2.7127, 2.6426, 4.0643]])

### Outer product

    v1 = torch.arange(1., 5.)
    v2 = torch.arange(1., 4.)
    torch.outer(v1, v2)
    
    tensor([[  1.,   2.,   3.],
     [  2.,   4.,   6.],
     [  3.,   6.,   9.],
     [  4.,   8.,  12.]])

## Only do one batch

    x,y = next(iter(data.train_dl))
    x.shape,y.shape

## Python file name peration

    path2fn = lambda path: re.search('\w*\.jpg$', path).group(0)  # \w means "any word character" * means "0 or more of the previous thing $<- end of the line