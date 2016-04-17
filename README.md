MyFarm
======

MyFarm is an app which helps to connect people from within the agricultural industrie.

package com.sky.parentalcontrolservice.api;

import com.sky.parentalcontrolservice.exception.TechnicalFailureException;
import com.sky.parentalcontrolservice.exception.TitleNotFoundException;

/**
 *
 * @author Helmut
 */
public interface MovieService {   
    String getParentalControlLevel(String movieId)
            throws TitleNotFoundException, TechnicalFailureException;    
}
    
package com.sky.parentalcontrolservice.api;

/**
 *
 * @author Helmut
 * @since 16/04/2016
 * @version 1.0
 * 
 * <p>returns true or false to the client</p>
 */  

public interface ParentalControlService {
  String getParentalControlLevelPreference(String movieId);
  public boolean hasPermissionToWatch();
}

package com.sky.parentalcontrolservice.exception;

/**
 *
 * @author Helmut
 */
public class TechnicalFailureException extends Exception {
     public TechnicalFailureException(String errorMessage, Throwable throwable) {
        super(errorMessage, throwable);
    }  
}

package com.sky.parentalcontrolservice.exception;

/**
 *
 * @author Helmut
 */
public class TitleNotFoundException extends Exception {
     public TitleNotFoundException(String errorMessage, Throwable throwable) {
        super(errorMessage, throwable);
    }    
}

package com.sky.parentalcontrolservice.impl;

/**
 *
 * @author Helmut
 */
public enum AcceptanceCriteria {
    MOVIE_NOT_FOUND,
    NO_PERMISSION_TO_WATCH   
}

package com.sky.parentalcontrolservice.impl;

/**
 *
 * @author Helmut
 */
public class ParentalControlLevel {
    
    
}

package com.sky.parentalcontrolservice.impl;

import com.sky.parentalcontrolservice.api.MovieService;
import com.sky.parentalcontrolservice.api.ParentalControlService;
import com.sky.parentalcontrolservice.exception.TechnicalFailureException;
import com.sky.parentalcontrolservice.exception.TitleNotFoundException;
import java.util.logging.Level;
import java.util.logging.Logger;

/**
 *
 * @author Helmut
 * 
 * <p></p>
 */
public class ParentalControlServiceImpl implements ParentalControlService { 
    
    private boolean isAllowed = false;
      
    private final MovieService movieService;

    public ParentalControlServiceImpl(MovieService movieService) {
        this.movieService = movieService;
    }
    
    private void allowanceMapping() {
        
    }

    @Override
    public String getParentalControlLevelPreference(String movieId) {
        
        
       return "";
    }

    @Override
    public boolean hasPermissionToWatch() {
        String movieId = null;
        try {
            if("".equals(movieService.getParentalControlLevel(movieId)))
            {return isAllowed=true;} else {return isAllowed = false;}
        } catch (TitleNotFoundException | TechnicalFailureException ex) {
            Logger.getLogger(ParentalControlServiceImpl.class.getName()).log(Level.SEVERE, null, ex);
        }
        return true;
    }
  
    
    
    
    
}
