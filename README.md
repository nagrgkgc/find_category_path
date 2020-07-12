# find_category_id_by_path

    /**
     * @var UrlFinderInterface
     */
    private $urlFinder;

    /**
     * ApplyCategoryIdsForLinkType constructor.
     * @param UrlFinderInterface $urlFinder
     */
    public function __construct(
        UrlFinderInterface $urlFinder
    ) {
        $this->urlFinder = $urlFinder;
        }

    /**
     * @param $link
     * @param $storeId
     * @return int|string
     */
    private function getCategoryId($link, $storeId)
    {
        $categoryUrl = 'men/shoes/test.html';

        $filterData = [
            UrlRewrite::REQUEST_PATH => $categoryUrl,
            UrlRewrite::STORE_ID => $storeId
        ];

        $urlRewrite = $this->urlFinder->findOneByData($filterData);
        if ($urlRewrite) {
            $entityId = $urlRewrite->getEntityId();
            return $entityId;
        }

        return '';
    }
