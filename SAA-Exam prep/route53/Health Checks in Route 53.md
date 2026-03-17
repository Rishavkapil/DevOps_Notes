Health check in route53 can only be applied to public endpoints. 

To apply a Health check to private Hosted zone , follow below : 

- Create a cloudwatch metric & asociate an alarm, then create a Health check that checks alarm itself. 

