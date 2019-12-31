# hello-world
tutorial repository

MARKET_CODE_DICT = {
    'kospi':'stockMKT',
    'kosdaq':'kosdaqMKT',
    'konex':'konexMKT'
    }
SEARCH_CODE_DICT = {
    '상장법인':'13',
    '관리종목':'01',
    '불성실공시종목':'05',
    'kospi200':'06',
    'krx100':'11'
    }

DOWNLOAD_URL = 'kine.krx.co.kr/corpgeneral/corpList.do'

def download_stock_codes(MarketType = None, SearchType = None):
    params = {'method':'download'}
    
    if MarketType.lower() in MARKET_CODE_DICT:
        params['marketType'] = MARKET_CODE_DICT[MarketType]
        
    if SearchType.lower() in SEARCH_CODE_DICT:
        params['searchType'] = SEARCH_CODE_DICT[SearchType]
        
    params_string = urlparse.encode(Params)
    request_url = urlparse.urlunsplit(['http', DOWNLOAD_URL, '', params_string, ''])
    
    df = pd.read_html(request_url, header=0)[0]

    
    return df
    
