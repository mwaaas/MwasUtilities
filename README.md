#### To upload a newer version
python setup.py sdist upload

#Utilities

###1. NotFound 

    ####### How to use it
    from MwasUtilities.utilities import not_found
    
    data = {"name":{"age":10}}
    
    data.get(name, not_found).get('height', not_found)
    
    
###2. LogDjangoSettingEnvironment

    ### How to use it
    from MwasUtilities.utilities import LogDjangoEnvironment
    
    LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'filters': {
        'environment': {
            '()':  LogDjangoEnvironment,
        },
    },
    'handlers': {
        'console': {
            'level': 'DEBUG',
            'class': 'logging.StreamHandler',
            'formatter': 'verbose',
            'filters':  ['environment'],
        },
    },
    'formatters': {
        'verbose': {
            'format': '%(asctime)s %(levelname)s module=%(module)s, '
                      'process_id=%(process)d, path=%(pathname)s, environment=%(environment)s, %(message)s'
        }
    },
    'loggers': {
        'django.request': {
            'handlers': ['sentry'],
            'level': 'ERROR',
        }
    }
}