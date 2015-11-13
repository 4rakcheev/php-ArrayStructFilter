/**
 * Class AStructFilter
 *
 * Класс позволяет производить поиск элементов списка по значениям полей этих элементов
 *
 * @property array $haystack Список структур
 * @property array $needleArgs Параметры со значениями для сравнения
 * @property string $condition Условие строгости поиска (range: OR, AND)
 *
 * @author Rakcheev Artem <4tema2@gmail.com>
 */
class AStructFilter {
 
    const CONDITION_OR='OR';
    const CONDITION_AND='AND';
 
    public $needleArgs;
    public $haystack;
    public $condition;
 
    public function __construct(array $haystack=array(), array $needleArgs=array(), $condition=self::CONDITION_OR)
    {
        $this->needleArgs = $needleArgs;
        $this->haystack = $haystack;
        $this->condition = $condition;
        return $this;
    }
 
    /**
     * @return array
     * @throws Exception при неизвестном условии @link self::CONDITION_
     */
    public function search()
    {
        if (empty($this->haystack) || empty($this->needleArgs)) {
            return $this->haystack;
        }
 
        switch ($this->condition) {
            case self::CONDITION_OR:
                $result = array_filter($this->haystack, array($this, 'filterORCondition'));
                break;
            case self::CONDITION_AND:
                $result = array_filter($this->haystack, array($this, 'filterANDCondition'));
                break;
            default:
                throw new Exception("Condition {$this->condition} not supported");
        }
 
        return $result;
    }
 
    private function filterORCondition($var)
    {
        is_object($var) && $var=(array)$var;
        foreach ($this->needleArgs as $key=>$val) {
            if (isset($var[$key]) && $var[$key] == $val) {
                return 1;
            }
        }
        return 0;
    }
 
    private function filterANDCondition($var)
    {
        is_object($var) && $var=(array)$var;
        foreach ($this->needleArgs as $key=>$val) {
            if (!isset($var[$key]) || $var[$key] != $val) {
                return 0;
            }
        }
        return 1;
    }
 
}
