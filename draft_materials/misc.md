```python
class InterpolationHandler:
    def __init__(self,
                 xpillars: List[str],
                 ypillars: List[float]) -> None:

        self._xpillars = xpillars
        self._ypillars = ypillars

    def pillars_dictionary(self):
        return dict(zip(self._xpillars, self._ypillars))

    def tenor_2_years(self, tenor_node: str):
        if tenor_node == '6M':
            return 0.5
        elif tenor_node == '7M':
            return 7 / 12
        elif tenor_node == '8M':
            return 8 / 12
        elif tenor_node == '9M':
            return 9 / 12
        elif tenor_node == '10M':
            return 10 / 12
        elif tenor_node == '3M':
            return 0.25
        elif tenor_node == '2M':
            return 2 / 12
        elif tenor_node == '1M':
            return 1 / 12
        elif tenor_node == '18M':
            return 1.5
        elif tenor_node=='5M':

            return 5/12
        elif tenor_node=='4M':

            return 4/12

        elif tenor_node=='11M':

            return 11/12

        elif tenor_node=='12M':

            return 1

        elif tenor_node=='15M':

            return 1.25

        elif tenor_node=='21M':

            return 1.75

        elif tenor_node=='2W':
            return 2/52
        else:
            return int(tenor_node[:-1])

    def ir_tenors_interpolation(self, tenor_node: int):
        x_pillars_num = [self.tenor_2_years(tenor_node) for tenor_node in self._xpillars]
        interp_object = interp1d(x_pillars_num, self._ypillars)
        pillars_dict = self.pillars_dictionary()

        if self.tenor_2_years(tenor_node) >= 10:
            # extrapolation
            return self._ypillars[-1]  # flat extrapoloation right end
        elif self.tenor_2_years(tenor_node) <= 0.25:
            return self._ypillars[0]  # flat extrapolation left end

        else:
            if tenor_node in self._xpillars:
                return pillars_dict[tenor_node]
            else:
                return float(interp_object(self.tenor_2_years(tenor_node)))
```
