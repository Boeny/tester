# tester
simplifies writing tests with mocha and chai

    require('tester')({
      'main config:': require('./config'),// describe
      'user config:': require('./params'),// describe

      'parse with user config:': {// describe
        'doesn\'t generate creatures by default (while {createAtStartCount: Number} is not set)': ()=>{// it
          return [new CreatureManager().pool.length, 0];
        },

        'static "create(index, params)" method creates a new creature': {// describe
          'which type is "object"': () => [typeof Creature.create(), 'object'],// it
          'with positive health': (assert)=>{// it
            assert.isAtLeast(Creature.create().health, 50);
          },
          'with positive offence': (assert)=>{// it
            assert.isAtLeast(Creature.create().offence, 0);
          },
          'with positive defence': (assert)=>{// it
            assert.isAtLeast(Creature.create().defence, 0);
          }
        }
      }
    });
