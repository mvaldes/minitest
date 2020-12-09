# minitest

Voici comment je ferais une app qui retrieve les derniers tweet d’un usagé basé sur un exemple trouvé sur internet:

un component contenant le corps des tweets avec des sous-component pour chaque élément 
(c’est mieux pour compréhension du code, pour la maintenance et la réutilisation).

ex: 


const myTweetContainer = (props) => {

  return(

    <div className="tweet-body">

      {props.children}

    </div>

  )

}



const myImage = (props) => {

  return(

    <img src={props.image} alt="Logo" className="picture">

    </img>

  )

}



const myHandle = (props) => {

  return(

    <div className="handle">

      {props.handle}

    </div>

  )

}



const myName = (props) => {

  return(

    <div className="name">

      {props.name}

    </div>

  )

}



const myTweet = (props) => {

  return(

    <div className="tweet">

      {props.tweet}

    </div>

  )

}



<tweetContainer>

      <div className="inner-body">

        <myImage image={props.image}/>

        <div className="body">

          <div className="inner-body">

            <myName name={props.name}/>

            <myHandle handle={props.handle}/>

          </div>

          <myTweet tweet={props.tweet}/>

        </div>

      </div>

    </tweetContainer>



un component qui va chercher les tweets dans un store (aimerais touché plus à un store) et appel le component tweetContainer


fetchTweeterUser() {

    fetch(tweeterAPI) // données dans un store

    .then(response => {

      if(response.ok) return response.json();

      throw new Error('Request failed.');

    })

    .then(data => {

      this.setState({

        users:[

          {

            name: data.results[0].name,

            image: data.results[0].picture.medium,

            tweet: data.results[0].email,

          },

          ...this.state.users,

        ]

      });

    })

    .catch(error => {

      console.log(error);

    });

  }



return(

            <TweetBody 

              key={index}

              name={name}

              handle={handle}

              tweet={tweet}

              image={image} />

          )
